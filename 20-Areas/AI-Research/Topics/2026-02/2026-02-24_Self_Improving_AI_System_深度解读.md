---
title: "Agent Orchestrator - 自我改进的AI编排系统"
author: prateek
source: https://x.com/agent_wrapper/status/2025986105485733945
date: 2026-02-24
type: evergreen-note
tags: [AI, Agent, Orchestrator, Self-Improving, Open-Source, Composio]
---

# Agent Orchestrator - 自我改进的AI编排系统

> **一句话定义**: 一个开源的自我改进型AI编排系统，使用8个可替换插件槽架构，在8天内由30个并行agents自主构建了40,000行TypeScript代码和3,288个测试，实现84.6% CI成功率的全自动开发流水线。

---

## 详细解释

### What
Agent Orchestrator是一个自我改进的AI开发系统：
- **核心特性**: 编排器本身就是一个AI Agent，而非脚本或仪表板
- **开发数据**: 40K行TypeScript + 17插件 + 3,288测试，8天内完成
- **人力投入**: ~3天实际专注工作，其余由agents填充
- **峰值产出**: 单日27 PRs合并（2026-02-14），完整平台发布
- **CI成功率**: 84.6%（41个失败全部自我纠正）
- **自动化评审**: 700条评审评论，agents自主修复68%

### Why
**核心问题**: Agents写得快，但人类成为瓶颈：
- 从写代码变成"照看写代码的东西"
- 检查CI、阅读评审、复制粘贴错误——这不可扩展
- 并行agents越多，人类管理负担越重

**解决方案**: 编排器Agent替代人类在循环中的角色：
- 持有所有活跃会话、PR、CI运行的上下文
- 自动转发失败和评审评论给对应agents
- 只在真正需要人类决策时才通知

### How
**从bash到TypeScript的进化**:
```
2500行bash脚本 (v0)
    ↓ (agents重写)
TypeScript v1 (基础编排器)
    ↓ (v1管理agents构建)
TypeScript v2 (当前版本)
    ↓ (持续自我改进)
递归优化循环...
```

**8插件槽架构（全部可替换）**:
| 槽位 | 功能 | 默认实现 | 可替换为 |
|------|------|----------|----------|
| 1 | Tracker | GitHub Issues | Linear |
| 2 | Workspace | Git worktree | Docker clone |
| 3 | Runtime | tmux session | Process/Docker/K8s |
| 4 | Agent | Claude-Code | Aider/Codex |
| 5 | Terminal | iTerm2观察 | Web dashboard |
| 6 | SCM | GitHub PR | 其他Git平台 |
| 7 | Reactions | 事件响应系统 | 自定义逻辑 |
| 8 | Notifier | Slack通知 | Telegram/其他 |

**完整工作流**:
```
Issue → Tracker拉取 → Workspace创建隔离环境
    ↓
Runtime启动tmux → Agent自主工作 → Terminal实时监控
    ↓
SCM创建PR → Reactions响应事件 → 失败则自动重派Agent
    ↓
Notifer只在需人工决策时通知
```

---

## 3个重要细节

### 1. 递归自我改进循环
这是系统的核心差异化特征：
```
Agents构建功能
    ↓
编排器观察什么有效
    ↓
调整未来会话的管理方式
    ↓
Agents构建更好的功能
    ↓
编排器再次被改进...
```

**自我改进系统 (ao-52)**:
- 记录每个会话的性能
- 跟踪会话结果
- 运行复盘（retrospectives）
- 学习哪些任务一次成功，哪些需要更紧的guardrails

**关键洞察**: 天花板不是"Claude-Code写TypeScript多厉害"，而是"系统能多有效地部署、观察和改进数十个并行agents"。

### 2. 智能事件响应系统 (Reactions)
自动化响应GitHub事件，无需人工 plumbing：
```yaml
reactions:
  ci_failed:
    action: spawn_agent
    prompt: "CI failed on this PR. Read the failure logs and fix the issues."

  changes_requested:
    action: spawn_agent
    prompt: "Review comments have been posted. Address each comment and push fixes."

  approved:
    action: notify
    channel: slack
    message: "PR approved and ready to merge."
```

**案例**: PR #125（dashboard重设计）经历12轮CI失败→修复循环，零人工干预，干净发布。

### 3. 真实状态检测（对抗Agent自我报告的不可靠性）
Claude-Code在每会话期间写入结构化JSONL事件文件：
- Agent是否在活跃生成tokens?
- 是否在等待工具执行?
- 是否空闲?
- 是否完成?

编排器直接读取这些文件，而非依赖Agent自我报告（"他们会撒谎，或至少会困惑"）。

**Git Trailers追踪**: 每提交通过git trailer标识编写模型：
- Opus 4.6: 复杂架构、跨包集成
- Sonnet: 插件实现、测试、文档（高容量）

---

## 架构图

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                          Agent Orchestrator                                 │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌────────────────────────────────────────────────────────────────────────┐ │
│  │                        编排器Agent (核心)                              │ │
│  │  • 读取代码库理解backlog                                              │ │
│  │  • 分解任务为可并行化子任务                                           │ │
│  │  • 分配任务给编码agents                                               │ │
│  │  • 监控进度，持有所有会话上下文                                       │ │
│  └──────────────────────────────────┬───────────────────────────────────┘ │
│                                       │                                      │
│  ┌──────────────────────────────────┴───────────────────────────────────┐ │
│  │                     8插件槽架构 (全部可替换)                           │ │
│  │                                                                         │ │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐        │ │
│  │  │Tracker  │ │Workspace│ │Runtime  │ │Agent    │ │Terminal │        │ │
│  │  │(GitHub) │ │(Workt.) │ │(tmux)   │ │(Claude) │ │(iTerm2) │        │ │
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘        │ │
│  │                                                                         │ │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐                                    │ │
│  │  │SCM      │ │Reactions│ │Notifier │                                    │ │
│  │  │(GitHub) │ │(Event)  │ │(Slack)  │                                    │ │
│  │  └─────────┘ └─────────┘ └─────────┘                                    │ │
│  │                                                                         │ │
│  └──────────────────────────────────┬───────────────────────────────────┘ │
│                                       │                                      │
│  ┌──────────────────────────────────┴───────────────────────────────────┐ │
│  │                     并行编码Agents (最多30并发)                        │ │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐      ┌──────────┐            │ │
│  │  │Agent #1  │ │Agent #2  │ │Agent #3  │ ...  │Agent #30 │            │ │
│  │  │• Worktree│ │• Worktree│ │• Worktree│      │• Worktree│            │ │
│  │  │• tmux    │ │• tmux    │ │• tmux    │      │• tmux    │            │ │
│  │  │• Isolated│ │• Isolated│ │• Isolated│      │• Isolated│            │ │
│  │  └──────────┘ └──────────┘ └──────────┘      └──────────┘            │ │
│  │                                                                         │ │
│  └──────────────────────────────────┬───────────────────────────────────┘ │
│                                       │                                      │
│  ┌──────────────────────────────────┴───────────────────────────────────┐ │
│  │                     自我改进系统 (ao-52)                                 │ │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐          │ │
│  │  │ Performance Log │  │ Retrospectives  │  │ Pattern Learning│          │ │
│  │  │ (会话结果追踪)   │  │ (定期复盘)      │  │ (成功模式识别)  │          │ │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘          │ │
│  │                              ↓                                          │ │
│  │  ┌──────────────────────────────────────────────────────────────┐      │ │
│  │  │ 优化循环: 观察 → 学习 → 调整 → 更好的agents → 更好的系统...   │      │ │
│  │  └──────────────────────────────────────────────────────────────┘      │ │
│  └────────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## 2条行动建议

### 建议1: 实现递归自我改进循环
在自己的AI系统中：
1. **记录信号**: 不要丢弃会话数据，记录哪些prompts产生干净PRs，哪些导致螺旋式失败
2. **定期复盘**: 设置自动化retrospective流程，识别成功模式和失败模式
3. **调整策略**: 根据历史数据调整任务分解方式、guardrails强度、模型选择
4. **闭环优化**: agents构建 → 编排器观察 → 系统改进 → agents构建更好功能

### 建议2: 采用8插件槽的可替换架构
设计系统时：
1. **识别8个核心功能域**: 问题追踪、工作空间、运行时、Agent、终端、SCM、响应、通知
2. **定义清晰接口**: 每个域有抽象接口，具体实现可替换
3. **从简单开始**: 先用GitHub+tmux+Claude-Code，后续按需替换
4. **事件驱动响应**: 用Reactions系统自动化处理CI失败、评审请求等事件

---

## 关联知识链接

- [[Topics/OpenClaw Agent Swarm]] - Elvis Sun的并行Agent实现
- [[Agent Orchestrator]] - 编排器概念
- [[Self-Improving System]] - 自我改进系统
- [[Plugin Architecture]] - 插件架构设计
- [[Recursive Improvement]] - 递归改进
- [[CI Auto-Fix]] - CI自动修复
- [[Multi-Agent Parallel]] - 多Agent并行
- [[Composio]] - Composio平台

---

## 参考原文

- 原文文件: [[../../50-Inbox/03-Processed/2026-02-24_Self_Improving_AI_System|原文存档]]
- X/Twitter: https://x.com/agent_wrapper/status/2025986105485733945
- GitHub: https://github.com/ComposioHQ/agent-orchestrator

---

*创建于: 2026-03-30 | 处理批次: 第一批-05*
