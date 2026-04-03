---
title: "Agent Tools Design"
type: evergreen
date: 2026-03-31
tags: [evergreen, AI, Agent, tools, MCP, design-principles, evaluation-driven, anthropic]
aliases: [Agent-Tools, Tool-Design, MCP-Tools-Design, Evaluation-Driven-Tools]
---

# Agent Tools Design

> **一句话定义**: Agent工具设计是Anthropic提出的评估驱动工程方法论——工具不再是传统的确定性函数调用，而是与非确定性Agent之间的新型软件契约，通过5大设计原则（整合功能、命名空间、语义上下文、Token效率、描述工程）和Build→Evaluate→Improve循环，构建Agent能够有效使用的工具系统。

---

## 详细解释

### 范式转变：新型软件契约

**核心洞察**:
> "Tools are a new kind of software which reflects a contract between deterministic systems and non-deterministic agents."

**传统软件 vs Agent工具**:

| 维度 | 传统软件/函数 | Agent工具 |
|------|--------------|-----------|
| **调用方** | 人类开发者 / 确定性系统 | 非确定性LLM Agent |
| **确定性** | 相同输入→相同输出 | 相同输入可能不同输出 |
| **契约类型** | 精确的函数签名 | 模糊的意图理解 |
| **错误处理** | 异常抛出，调用方处理 | Agent可能误解或幻觉 |
| **设计理念** | 暴露完整功能 | 匹配Agent认知特点 |

**设计目标**:
> "Increase the surface area over which agents can be effective in solving a wide range of tasks by using tools to pursue a variety of successful strategies."

---

## 评估驱动的工具开发流程

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    评估驱动的工具开发循环 (Build→Evaluate→Improve)         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     Phase 1: Build (构建原型)                    │   │
│   │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│   │                                                                  │   │
│   │   • 快速原型开发                                                 │   │
│   │   • 本地MCP服务器/DXT扩展测试                                    │   │
│   │   • 使用Claude Code验证工具可用性                                │   │
│   │   • 手动测试发现粗糙边缘                                         │   │
│   │   • 收集真实用户反馈                                             │   │
│   │                                                                  │   │
│   └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                     │
│                                    ▼                                     │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     Phase 2: Evaluate (运行评估)                 │   │
│   │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│   │                                                                  │   │
│   │   Step 1: 生成评估任务                                           │   │
│   │   ├── 强任务：真实场景、复杂多步、可验证                         │   │
│   │   └── 弱任务（避免）：过于简单、单一工具调用                     │   │
│   │                                                                  │   │
│   │   Step 2: 设计验证器                                             │   │
│   │   ├── 精确字符串比较                                             │   │
│   │   ├── Claude作为评判员                                          │   │
│   │   └── 避免过度严格（格式、标点差异）                             │   │
│   │                                                                  │   │
│   │   Step 3: 运行评估循环                                           │   │
│   │   ├── 收集：accuracy、runtime、tool_calls、tokens、errors        │   │
│   │   └── 推荐：使用interleaved thinking增强推理                     │   │
│   │                                                                  │   │
│   └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                     │
│                                    ▼                                     │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     Phase 3: Improve (协作改进)                    │   │
│   │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│   │                                                                  │   │
│   │   分析方法:                                                      │   │
│   │   • 观察Agent困惑点                                              │   │
│   │   • 读取评估Agent的reasoning和feedback                           │   │
│   │   • 审查原始transcripts                                          │   │
│   │   • 分析工具调用指标（冗余调用→优化分页/令牌限制）               │   │
│   │                                                                  │   │
│   │   让Agent改进工具:                                               │   │
│   │   • 将评估transcripts粘贴到Claude Code                           │   │
│   │   • Claude分析并重构工具                                         │   │
│   │   • 使用held-out test set防止过拟合                              │   │
│   │                                                                  │   │
│   └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                     │
│                                    └────────────────────────────────────▶
│                                          (循环回到Build或Evaluate)
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 五大设计原则

### 原则1：选择正确的工具（Less is More）

**核心洞察**: Agent的context有限，不能像传统软件那样暴露所有底层操作。

**设计对比**:

| 传统API思维 | Agent工具思维 | 原因 |
|------------|--------------|------|
| `list_contacts` | `search_contacts` | Agent不应逐条遍历 |
| `list_users` + `list_events` + `create_event` | `schedule_event` | 整合常用工作流 |
| `read_logs` | `search_logs` | 只返回相关行+上下文 |
| `get_customer_by_id` + `list_transactions` + `list_notes` | `get_customer_context` | 一次性编译相关信息 |

**关键洞察**:
> "Tools can consolidate functionality, handling potentially multiple discrete operations (or API calls) under the hood."

**好处**:
- 减少context消耗
- 降低Agent犯错概率
- 符合人类自然工作方式

---

### 原则2：命名空间划分

**问题**: 当Agent可访问数百个工具时，功能重叠会导致困惑。

**命名策略对比**:

| 策略 | 示例 | 效果 |
|------|------|------|
| **无命名空间** | `search` | 模糊，Agent不知选择哪个 |
| **服务前缀** | `asana_search`, `jira_search` | 按服务区分 |
| **资源后缀** | `asana_projects_search`, `asana_users_search` | 按资源细分 |

**研究发现**:
> "We have found selecting between prefix- and suffix-based namespacing to have non-trivial effects on our tool-use evaluations. Effects vary by LLM."

---

### 原则3：返回有意义的上下文（语义标识符）

**关键洞察**: Agent更擅长处理自然语言而非技术标识符。

**UUID问题示例**:
```
❌ 低效: "user_id": "550e8400-e29b-41d4-a716-446655440000"
✅ 高效: "user_name": "Jane Smith", "user_index": 42
```

**研究发现**:
> "Merely resolving arbitrary alphanumeric UUIDs to more semantically meaningful and interpretable language (or even a 0-indexed ID scheme) significantly improves Claude's precision in retrieval tasks by reducing hallucinations."

**ResponseFormat枚举**:
```typescript
enum ResponseFormat {
  DETAILED = "detailed",  // 206 tokens - 包含所有ID和元数据
  CONCISE = "concise"     // 72 tokens (~1/3) - 仅内容
}
```

**实际效果**: Slack工具使用concise模式节省约2/3 tokens。

---

### 原则4：优化Token效率

**Claude Code默认限制**: 25,000 tokens/工具响应

**优化策略**:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    Token效率优化策略                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. 分页 (Pagination)                                                   │
│     • 默认返回合理数量                                                   │
│     • 提供page/page_size参数                                             │
│                                                                          │
│  2. 范围选择 (Range Selection)                                          │
│     • 日期范围                                                            │
│     • 数量限制 (limit=N)                                                  │
│                                                                          │
│  3. 过滤 (Filtering)                                                    │
│     • 关键词过滤                                                          │
│     • 类型过滤                                                            │
│                                                                          │
│  4. 智能截断 (Smart Truncation)                                         │
│     • 保留头尾关键信息                                                    │
│     • 标明总长度和截断位置                                                │
│                                                                          │
│  5. 错误响应工程化                                                        │
│     ❌ 低效: "Error 404"                                                 │
│     ✅ 高效: "未找到用户'John'。请检查拼写或使用search_users模糊搜索。"    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

### 原则5：Prompt Engineering工具描述

**核心原则**: 像给新员工做入职培训一样描述工具。

**最佳实践对比**:

| 方面 | ❌ 差示例 | ✅ 好示例 |
|------|----------|----------|
| **参数命名** | `user` | `user_id` |
| **描述清晰度** | "获取用户" | "通过用户ID获取用户详情，ID格式为数字" |
| **隐式知识** | 假设Agent知道 | 明确说明专业术语、查询格式 |
| **数据模型** | 松散验证 | 严格schema，明确输入输出 |

**成功案例**:
> "Claude Sonnet 3.5 achieved state-of-the-art performance on the SWE-bench Verified evaluation after we made precise refinements to tool descriptions, dramatically reducing error rates and improving task completion."

---

## 架构图

### 完整Agent工具工程架构

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    Agent工具工程五层架构                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                     工具层 (Tools)                                │   │
│  │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│  │                                                                  │   │
│  │   • 整合功能：将多步操作合并为单一工具                              │   │
│  │   • 命名空间：asana_tasks_search vs search                         │   │
│  │   • 语义上下文：name而非UUID                                       │   │
│  │                                                                  │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                    │
│                                    ▼                                    │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                     效率层 (Efficiency)                         │   │
│  │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│  │                                                                  │   │
│  │   • 分页: page=1&limit=20                                       │   │
│  │   • 范围: date_from=2024-01-01                                  │   │
│  │   • 过滤: keyword=urgent                                        │   │
│  │   • 截断: [head...tail] with total info                         │   │
│  │   • 格式: ResponseFormat.CONCISE/DETAILED                       │   │
│  │                                                                  │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                    │
│                                    ▼                                    │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                     契约层 (Contract)                           │   │
│  │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│  │                                                                  │   │
│  │   Tool Description (Prompt Engineering)                        │   │
│  │   • 明确命名: user_id vs user                                    │   │
│  │   • 详细描述: 用途、参数、返回值                                   │   │
│  │   • 示例说明: 输入输出示例                                       │   │
│  │   • 错误指导: 如何修正错误                                       │   │
│  │   • 术语解释: 专业术语定义                                       │   │
│  │                                                                  │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                    │
│                                    ▼                                    │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                     评估层 (Evaluation)                         │   │
│  │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│  │                                                                  │   │
│  │   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐      │   │
│  │   │   强任务     │───▶│   评估循环   │───▶│   分析改进   │      │   │
│  │   │   设计       │    │   执行       │    │   迭代       │      │   │
│  │   └──────────────┘    └──────────────┘    └──────────────┘      │   │
│  │                                                                  │   │
│  │   关键指标:                                                       │   │
│  │   • Accuracy (准确性)                                             │   │
│  │   • Token consumption (Token消耗)                                 │   │
│  │   • Tool call patterns (调用模式)                                 │   │
│  │   • Error rates (错误率)                                          │   │
│  │   • Runtime (运行时间)                                            │   │
│  │                                                                  │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                    │                                    │
│                                    ▼                                    │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                     优化层 (Optimization)                       │   │
│  │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  │   │
│  │                                                                  │   │
│  │   • 分析transcripts                                               │   │
│  │   • 重构多个工具                                                  │   │
│  │   • 保持一致性                                                    │   │
│  │   • 防止过拟合 (held-out test set)                               │   │
│  │                                                                  │   │
│  │   结果: 即使是专家编写的工具，评估优化仍能提取额外性能             │   │
│  │                                                                  │   │
│  └──────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   ═══════════════════════════════════════════════════════════════════  │
│   核心机制: 工具设计 + 评估驱动 + 持续优化 = 有效Agent工具                │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 核心数据

| 指标 | 数值/描述 | 来源 |
|------|----------|------|
| **25,000** | Claude Code默认token限制 | 工具响应上限 |
| **1/3** | Token节省 | Slack工具concise模式 |
| **206 vs 72** | Token对比 | detailed vs concise响应 |
| **~50** | Claude Code系统指令数 | 占用可用指令容量1/3 |
| **150-200** | Frontier模型可跟随指令数 | 研究数据 |
| **SOTA** | Claude Sonnet 3.5成绩 | SWE-bench Verified |
| **3大** | 评估阶段 | Build→Evaluate→Improve |
| **5大** | 设计原则 | 工具设计指南 |

---

## 行动建议

### 对工具设计者

1. **采用评估驱动开发**
   - 先建立原型验证工具可用性
   - 设计真实复杂度的评估任务（避免简单sandbox）
   - 使用held-out test set防止过拟合

2. **整合相关操作**
   - 将常用多步操作合并为单一工具
   - 例如：`schedule_event` 替代 `list_users`+`list_events`+`create_event`
   - 减少Agent的context消耗和决策负担

3. **设计语义标识符**
   - 将UUID替换为人类可读名称
   - 使用0-indexed ID替代随机字符串
   - 显著减少幻觉，提高检索精度

4. **实现ResponseFormat**
   - 提供CONCISE和DETAILED两种模式
   - CONCISE用于正常操作（节省token）
   - DETAILED用于需要下游工具调用的场景（保留必要ID）

5. **优化token效率**
   - 实现分页、范围选择、过滤
   - 使用智能截断（保留头尾关键信息）
   - 工程化错误响应（指导修正而非返回错误码）

6. **工程化工具描述**
   - 像给新员工培训一样描述工具
   - 明确参数命名（`user_id` vs `user`）
   - 提供输入输出示例
   - 解释专业术语

### 对MCP服务器开发者

7. **使用命名空间**
   - 按服务前缀：`asana_search`, `jira_search`
   - 按资源后缀：`asana_projects_search`, `asana_users_search`
   - 测试不同命名策略对你使用的LLM的效果

8. **添加工具注解**
   - 使用MCP tool annotations
   - 标明需要开放世界访问的工具
   - 标明破坏性变更工具

---

## 关联概念

- [[MCP]] — Model Context Protocol
- [[Agent-Tools]] — Agent工具概念
- [[Tool-Design]] — 工具设计原则
- [[Token-Efficiency]] — Token效率优化
- [[Prompt-Engineering]] — Prompt工程
- [[Evaluation-Driven-Development]] — 评估驱动开发
- [[Semantic-Identifiers]] — 语义标识符
- [[ResponseFormat]] — 响应格式
- [[Held-out-Test-Set]] — 保留测试集
- [[Interleaved-Thinking]] — 交错思考
- [[Claude-Code]] — Claude Code
- [[SWE-bench]] — SWE-bench评估
- [[12-Factor-Agents]] — 12 Factor Agents原则

---

## 来源与扩展阅读

- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-29_Writing_effective_tools_for_AI_agents_深度解读]] — Anthropic工具设计深度解读
- 原文：https://www.anthropic.com/engineering/writing-tools-for-agents

---

## 关键引用

> "Tools are a new kind of software which reflects a contract between deterministic systems and non-deterministic agents."

> "像给新员工做入职培训一样描述工具。"

> "Claude Sonnet 3.5通过工具描述优化在SWE-bench达到SOTA。"

> "将常用多步操作合并为单一工具，直接解决Agent context有限的约束。"

---

## 标签

#evergreen #Agent-Tools #Tool-Design #MCP #Evaluation-Driven #Anthropic #Token-Efficiency
