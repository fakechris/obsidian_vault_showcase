---
title: "AI Agent"
type: evergreen
date: 2026-03-30
tags: [evergreen, AI, Agent]
aliases: [AI-Agent, Agent]
---

# AI Agent

> **一句话定义**: AI Agent 是能够感知环境、自主决策并采取行动以实现特定目标的 AI 系统——但**核心洞察是Agent本身没有智能**，它是人和语言模型之间的中间层，做的是上下文管理和工具编排。

---

## 📝 详细解释

### Agent ≠ 模型

**关键认知**:
```
Agent框架 ≠ 智能
Agent = 中间层程序 (运行在你电脑上)
    ↓
转发消息给后端模型 (Claude/GPT/Gemini)
    ↓
把回复传回用户
```

> **换模型 = 换能力**: 用差模型什么都做不了，换最新模型能力爆表。

---

## Agent 六大机制

### 1. System Prompt (人格构造)

**4000+ tokens 的身份定义**:
- 人格/行为准则
- 可用工具描述
- Skill 索引

> 每次请求都拼在消息前面，是Agent的"宪法"

### 2. Tool Calling (执行能力)

**最强大工具**: `execute` (可执行任意 shell command)

**安全风险**:
- YouTube 留言可以触发修改本地文件
- 任意命令执行 = 极大攻击面

**防御**:
- memory.md 写明行为边界
- 关键操作人类确认

### 3. SubAgent (任务分解)

**Spawn机制**:
```
父Agent ──► Spawn子Agent ──► 执行任务
    │           │
    │           ▼
    │      中间过程不进父context
    │           │
    │           ▼
    └────── 接收最终摘要
```

**限制**: 禁止子代再 spawn，防止无限外包

### 4. Skill (标准流程)

**本质**: 文本文件(.md)，不是程序

**按需加载** (Progressive Disclosure):
```
System Prompt只放Skill索引
    ↓
需要时Read加载完整Skill
    ↓
不浪费context window
```

**安全警告**: 341/3000个公开Skill包含恶意内容（11%）

### 5. Memory (持久记忆)

**机制**:
```
每次会话清空 (context window重置)
    ↓
重要事项 → 调用写入工具 → memory.md
    ↓
下次会话自动加载memory.md
```

**弱模型陷阱**: 说"记住了"但没调用写入工具 = 记了个寂寞

### 6. Heartbeat + Context Engineering

**Heartbeat**: 定时自动触发，读 habit.md 执行定时任务

**Compaction风险**:
```
Meta研究员案例:
"删除前要确认"指令 ──► Context Compaction ──► 指令被摘要掉
    │
    ▼
Agent自动删除文件，无确认
```

**关键指令应写入**: memory.md 或 System Prompt (不会被compaction删掉)

---

## Agent 工作循环

```
感知 (Perceive) → 思考 (Think) → 行动 (Act)
     ↑                              ↓
     └────── 记忆/状态更新 ←────────┘
```

---

## Agent 类型

| 类型 | 特点 | 示例 |
|------|------|------|
| **Task Agent** | 完成特定任务 | Claude Code, Coding Agent |
| **Research Agent** | 信息收集与分析 | Perplexity, Research Assistant |
| **Orchestrator Agent** | 协调多 Agent | Multi-Agent 系统 |
| **Autonomous Agent** | 长期自主运行 | AutoGPT (早期探索) |
| **Multi-Agent Team** | 多角色协作 | OpenClaw 5角色系统 |

---

## 关键挑战

- **可靠性**: 如何确保 Agent 不犯错
- **安全性**: 如何防止 Agent 造成损害 (execute工具风险)
- **可控性**: 人类如何保持监督权
- **长期记忆**: Agent 如何记住长期任务
- **协作编排**: 多 Agent 如何有效分工协作
- **Context Compaction**: 重要指令被摘要丢失的风险

---

## 安全最佳实践

```
1. 理解Agent就是中间层
   └── 不要神化Agent框架

2. 关键指令写入安全位置
   └── memory.md 或 System Prompt

3. Skill安全审查
   └── 社区Skill 11%有恶意内容

4. 给Agent安全的执行环境
   ├── 专属电脑
   ├── 独立账号
   └── 关键操作人类确认
```

---

## 🔗 关联概念

- [[Agent-Harness]] — Agent 的基础设施框架
- [[Agent-Memory]] — Agent 的记忆系统
- [[MCP]] — Agent 与工具连接的标准
- [[Claude-Code]] — 代码 Agent 的参考实现
- [[Agent-Orchestrator]] — 多 Agent 编排系统
- [[Multi-Agent-Collaboration]] — 多 Agent 协作模式
- [[Context-Engineering]] — 上下文工程
- [[Context-Compaction]] — 上下文压缩风险

---

## 📚 来源与扩展阅读

- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-11_Lee_Hung_Yi_OpenClaw_Agent_Anatomy_深度解读]] — 李宏毅讲透AI Agent运作原理
- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-29_12_Factor_Agents_深度解读]] — 12 Factor Agents设计原则
- [[2026-03-01_Agent_Harness_is_the_Real_Product_解读]] — Agent Harness概念
- [[2026-02-22_Agent_Skills_Context_Engineering_解读]] — Skill与Progressive Disclosure

---

## 💡 核心洞察

> **核心洞察**: AI Agent本身没有智能，它是人和语言模型之间的中间层。Agent的"聪明程度"完全取决于背后的模型，Agent框架做的是**上下文管理、工具编排、记忆持久化**。真正的智能来自LLM，Agent只是让这种智能能够安全、可靠、持续地作用于真实世界。

---

*创建于 2026-03-30，补充于 2026-03-31，精读深度解读提取*
