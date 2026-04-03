---
title: "Agent Architecture"
type: evergreen
date: 2026-03-31
tags: [evergreen, AI, Agent, Architecture, System-Design]
aliases: [Agent-Architecture, System-Architecture, 架构设计]
---

# Agent Architecture

> **一句话定义**: Agent架构是设计AI代理系统的分层工程框架——通过控制流层、核心循环层、记忆层、Harness层、多Agent层、评估层的六层解耦，实现从简单Workflow到复杂Multi-Agent系统的可扩展、可维护、可观测的工程化落地。

---

## 六层架构概览

```
┌─────────────────────────────────────────────────────────────────────────┐
│                      Agent Engineering System                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  1. Control Flow Layer         ← 编排模式选择                          │
│  2. Agent Core Loop            ← 感知-决策-行动-反馈循环                │
│  3. Memory Layer               ← 四层记忆系统                            │
│  4. Harness Layer              ← 验证与约束基础设施                      │
│  5. Multi-Agent Layer          ← 多Agent协作                            │
│  6. Evaluation Layer           ← 评测与可观测性                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Layer 1: Control Flow (控制流层)

**模式选择**（从简单到复杂）:

| 模式 | 控制方 | 适用场景 |
|------|--------|----------|
| **Prompt Chaining** | 代码 | 线性步骤，固定流程 |
| **Routing** | 代码 | 输入分类，分发处理 |
| **Parallelization** | 代码 | 分治/投票，并发执行 |
| **Orchestrator-Workers** | 混合 | 动态分解，委派执行 |
| **Evaluator-Optimizer** | 混合 | 迭代优化，质量提升 |
| **Full Agent** | LLM | 开放性问题，动态决策 |

**关键原则**: "很多场景并不需要完整的Agent自主权，把其中几种模式搭起来就够了。"

---

## Layer 2: Agent Core Loop (核心循环层)

**Agent Loop 本质**:
```
感知(Perceive) → 决策(Decide) → 行动(Act) → 反馈(Observe)
        ↑                                      ↓
        └────────────── 循环 ──────────────────┘
```

**核心循环不到20行代码**:
```typescript
while (true) {
  const response = await llm.create({
    tools: toolDefinitions,
    messages,
  });

  if (response.stop_reason === "tool_use") {
    const results = await executeTools(response.content);
    messages.push({ role: "assistant", content: response.content });
    messages.push({ role: "user", content: results });
  } else {
    return response.content;
  }
}
```

**关键原则**: "不应该让循环体本身变成一个巨大的状态机，模型负责推理，外部系统负责状态和边界。"

---

## Layer 3: Memory Layer (记忆层)

**四层记忆架构**:

| 记忆类型 | 存储位置 | 生命周期 | 用途 |
|----------|----------|----------|------|
| **工作记忆** | messages[] | 当前会话 | 对话上下文 |
| **程序性记忆** | Skills文件 | 按需加载 | 操作流程、领域规范 |
| **情景记忆** | JSONL历史 | 持久化 | 发生了什么，支持检索 |
| **语义记忆** | MEMORY.md | 跨会话 | Agent主动写入重要事实 |

**记忆整合流程**:
```
对话流持续增长
      ↓
tokenUsage / maxTokens >= 0.5 (触发阈值)
      ↓
成功路径: LLM摘要 → 追加MEMORY.md
失败路径: 原始消息写入archive/
```

---

## Layer 4: Harness Layer (验证层)

**Harness 四要素**:

| 要素 | 功能 | 实例 |
|------|------|------|
| **验收基线** | 明确完成标准 | 单元测试、类型检查 |
| **执行边界** | 沙箱、超时、权限 | Docker、seccomp |
| **反馈信号** | 执行结果可见 | 日志、trace、metrics |
| **回退手段** | 失败恢复机制 | 重试、回滚、人工介入 |

**核心结论**: "这些不是AI问题，是基础设施问题。"

---

## Layer 5: Multi-Agent Layer (多Agent层)

**多Agent组织的正确顺序**:
```
协议 → 隔离 → 协作 → 并行
```

**三层协议**:
1. **JSONL消息队列**: 结构化通信
2. **.tasks/任务图**: 依赖关系管理
3. **.worktrees/**: 文件修改隔离

**指挥者 vs 统筹者模式**:

| 维度 | 指挥者模式 | 统筹者模式 |
|------|-----------|-----------|
| 协作方式 | 同步 | 异步 |
| 人参与 | 每轮互动 | 只在起点和终点 |
| 产出 | 短暂 | 持久化（分支、PR） |
| 价值 | 实时调整 | 规模化并行 |

---

## Layer 6: Evaluation Layer (评估层)

**能力评测 vs 回归测试**:

| 维度 | 能力评测 | 回归测试 |
|------|----------|----------|
| 目的 | 找能力上限 | 防功能退化 |
| 指标 | Pass@k | Pass^k |
| 通过标准 | k次至少1次对 | k次必须全对 |

**两层可观测性**:
```
第一层: 人工抽样 (10-20%流量)
   └── 摸清失败模式

第二层: LLM自动 (其余流量)
   └── 全量覆盖，规模化分析
```

---

## OpenClaw 四层解耦架构实例

| 层级 | 职责 | 关键设计 |
|------|------|----------|
| **Gateway** | WebSocket服务，消息路由 | Channel与Agent不直接通信 |
| **Channel适配器** | 23+渠道统一接口 | 新增渠道不改Agent代码 |
| **Pi Agent** | 主循环、会话状态、调度 | 核心循环与渠道解耦 |
| **工具集** | shell/fs/web/browser/MCP | ACI原则设计 |
| **上下文+记忆** | Skills延迟加载 + MEMORY.md | 50% token阈值自动整合 |

**消息总线模式**:
```typescript
// 入站消息结构，Agent不知道来自哪个平台
const inbound = { channel, session_key, content };

// 每个渠道只需实现三个方法
class ChannelAdapter {
  start() {}
  stop() {}
  send(session_key, text) {}
}
```

---

## 路由与Bindings配置

**路由优先级**（从具体到一般）:
```
1. peer + guildId + accountId + channel
2. guildId + accountId + channel
3. accountId + channel
4. channel
5. 默认Agent
```

**Bindings偷懒艺术**:
> "多Agent前先考虑bindings——同一Agent在不同场景用不同模型"

```yaml
# 同一Agent，不同场景用不同模型
agents:
  assistant:
    model: claude-sonnet-4-6  # 默认

bindings:
  # 日常闲聊用轻量级
  - channel: discord
    accountId: "chat-bot"
    agentId: assistant
    modelOverride: claude-haiku-4-5

  # 研发设计用最强模型
  - channel: discord
    guildId: "dev-guild"
    accountId: "design-bot"
    agentId: assistant
    modelOverride: claude-opus-4-6
```

---

## 关联概念

- [[Workflow]] — 控制流层的模式选择
- [[Deep-Agents]] — 完整自主Agent的实现
- [[Agent-Memory]] — 四层记忆系统详解
- [[Harness-Engineering]] — 验证层基础设施
- [[Multi-Agent]] — 多Agent协作模式
- [[OpenClaw]] — 四层解耦架构实例
- [[Context-Engineering]] — 上下文管理技术

---

## 来源引用

- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-31_Tw93_Agent_Engineering_深度解读]] — Agent工程六层架构
- [[../../20-Areas/AI-Research/Topics/2026-02/2026-02-20_OpenClaw多Agent配置实战_深度解读]] — 路由、Bindings、权限控制

---

*创建于 2026-03-31，精读 2 篇深度解读提取*
