---
title: "ComposioHQ/agent-orchestrator: 并行AI Agent编排层 (1.4k stars)"
github: "https://github.com/ComposioHQ/agent-orchestrator"
owner: ComposioHQ
repo: agent-orchestrator
date: 2026-02-21
batch_date: 2026-02-21
type: github-project
tags: [github, typescript, agent, orchestration, claude-code, codex, aider]
pinboard_tags: [agent, orchestration]
source_used: github-readme-extract
source_url: "https://github.com/ComposioHQ/agent-orchestrator"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# ComposioHQ/agent-orchestrator: 并行AI Agent编排层

## 一句话概述

管理并行AI coding agent舰队的编排层，每个agent在独立的git worktree中工作，自动修复CI失败、处理审查评论并创建PR，通过统一仪表板监控。

## 项目定位

**目标用户**:
- 需要并行管理多个AI agent的团队
- 希望自动化CI修复和PR处理的开发者
- 使用Claude Code、Codex、Aider等agent的用户
- 寻求agent工作流编排的工程师

**解决的问题**:
- **手动协调负担**: 同时管理多个agent工作流困难
- **反馈循环延迟**: CI失败和审查评论响应慢
- **上下文隔离**: 多任务并行时上下文干扰
- **状态追踪困难**: 难以掌握多个agent工作状态

**使用场景**:
- 批量处理多个issue/PR
- 自动化CI修复工作流
- 并行代码审查处理
- 大规模代码重构任务

**与同类项目差异**:
- **多Agent并行**: 同时运行多个agent，各在独立worktree
- **自动反馈处理**: CI失败和审查评论自动路由给agent
- **通用编排层**: 支持多种agent（Claude Code, Codex, Aider）
- **插件架构**: 7个插件槽位，可扩展runtime/agent/tracker

## README 中文简介

**Agent Orchestrator** — 并行AI coding agent编排层

管理在代码库上并行工作的AI coding agent舰队。每个agent获得自己的git worktree、分支和PR。CI失败时agent自动修复，审查者留下评论时agent处理回应——你只需要在人类判断需要时介入。

**Agent-agnostic** (Claude Code, Codex, Aider) · **Runtime-agnostic** (tmux, Docker) · **Tracker-agnostic** (GitHub, Linear)

**工作原理**:
1. **启动** — `ao start` 启动仪表板和编排器agent
2. **生成工作器** — 每个issue获得独立agent和隔离worktree
3. **自主工作** — agent读取代码、编写测试、创建PR
4. **处理反馈** — CI失败和审查评论自动路由给agent
5. **审查合并** — 只需在人类判断需要时介入

**快速开始**:
```bash
npm install -g @composio/ao
ao start https://github.com/your-org/your-repo
# 仪表板在 http://localhost:3000 打开
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 并行Agent | 同时运行多个agent | README | 高 |
| Git Worktree隔离 | 每个agent独立工作区 | README | 高 |
| CI自动修复 | CI失败自动路由给agent | README | 高 |
| 审查评论处理 | 评论自动触发agent响应 | README | 高 |
| 多Agent支持 | Claude Code, Codex, Aider | README | 高 |
| 插件系统 | 7个可扩展插件槽位 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Agent Orchestrator 架构                       │
│           (并行AI Agent编排层)                              │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              仪表板层 (Web UI)                     │  │
│  │                                                  │  │
│  │   • 项目状态监控                                 │  │
│  │   • Agent状态展示                                │  │
│  │   • PR/Issue追踪                                 │  │
│  │   • 人工介入触发                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              编排器层 (Orchestrator Agent)         │  │
│  │                                                  │  │
│  │   • 任务分发                                     │  │
│  │   • Worker生成                                   │  │
│  │   • 反馈路由                                     │  │
│  │   • 状态管理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Worker层 (多个并行Agent)              │  │
│  │                                                  │  │
│  │   ┌──────────┬──────────┬──────────┬──────────┐│  │
│  │   │ Agent 1  │ Agent 2  │ Agent 3  │ Agent N  ││  │
│  │   │ Worktree │ Worktree │ Worktree │ Worktree ││  │
│  │   │ Branch   │ Branch   │ Branch   │ Branch   ││  │
│  │   └──────────┴──────────┴──────────┴──────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              插件层 (7个槽位)                      │  │
│  │                                                  │  │
│  │   ┌────────┬────────┬────────┬────────┐      │  │
│  │   │Runtime │ Agent  │Workspace│Tracker │      │  │
│  │   │Notifier│ Terminal│        │        │      │  │
│  │   └────────┴────────┴────────┴────────┘      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心编排 | `packages/core/` | 编排逻辑和类型定义 | 核心 |
| AO CLI | `packages/cli/` | 命令行接口 | 核心 |
| 仪表板 | `packages/dashboard/` | Web UI | 核心 |
| 插件系统 | `packages/plugins/` | 运行时/agent/tracker插件 | 扩展 |
| 示例 | `examples/` | 配置模板 | 参考 |

## 运行与开发方式

**安装**:
```bash
npm install -g @composio/ao
```

**从源码安装**:
```bash
git clone https://github.com/ComposioHQ/agent-orchestrator.git
cd agent-orchestrator && bash scripts/setup.sh
```

**启动**:
```bash
# 新项目
ao start https://github.com/your-org/your-repo

# 现有本地项目
cd ~/your-project && ao start

# 添加更多项目
ao start ~/path/to/another-repo
```

**开发**:
```bash
pnpm install && pnpm build    # 安装和构建
pnpm test                      # 运行测试 (3,288测试用例)
pnpm dev                       # 启动仪表板开发服务器
```

## 外部接口

**CLI命令**:
| 命令 | 说明 |
|------|------|
| `ao start [repo]` | 启动编排器和仪表板 |
| `ao config-help` | 查看配置schema |

**配置文件** (`agent-orchestrator.yaml`):
```yaml
port: 3000
defaults:
  runtime: tmux
  agent: claude-code
  workspace: worktree
  notifiers: [desktop]

projects:
  my-app:
    repo: owner/my-app
    path: ~/my-app
    defaultBranch: main

reactions:
  ci-failed:
    auto: true
    action: send-to-agent
    retries: 2
  changes-requested:
    auto: true
    action: send-to-agent
    escalateAfter: 30m
```

**插件架构**:
| 槽位 | 默认 | 替代方案 |
|------|------|----------|
| Runtime | tmux | process |
| Agent | claude-code | codex, aider, opencode |
| Workspace | worktree | clone |
| Tracker | github | linear, gitlab |
| SCM | github | gitlab |
| Notifier | desktop | slack, discord, webhook |
| Terminal | iterm2 | web |

## 数据流 / 控制流

```
用户: ao start
    ↓
编排器Agent启动
    ↓
监听GitHub Issues
    ↓
检测到新Issue
    ↓
生成Worker Agent + Git Worktree
    ↓
Agent自主工作 → 创建PR
    ↓
监听CI状态 / 审查评论
    ↓
[CI失败] → 路由给Agent修复
[审查评论] → 路由给Agent回应
    ↓
[通过] → 通知用户合并
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 | 高 |
| Node.js | 运行时 | 高 |
| pnpm | 包管理器 | 高 |
| tmux | 默认运行时 | 高 |
| Git Worktree | 工作区隔离 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细文档，有示例配置 | 高 |
| 上手难度 | 低 | npm install -g 即可 | 低 |
| 架构复杂度 | 高 | 插件系统+编排逻辑 | 高 |
| 外部依赖 | 中 | 依赖Node.js和Git | 中 |
| Stars | 中 | 1.4k stars | 中 |
| 维护状态 | 高 | Composio官方项目，活跃 | 高 |

**统计指标**:
- PRs合并: 61
- 测试用例: 3,288
- 社区: Discord活跃

**风险提示**:
- ⚠️ **资源消耗**: 并行运行多个agent资源占用大
- ⚠️ **复杂性**: 编排层增加了系统复杂度
- ⚠️ **成本**: 多agent并行可能产生较高API费用

## 关联概念

- [[Agent-Orchestration]] - Agent编排模式
- [[Git-Worktree]] - Git工作树隔离
- [[Claude-Code]] - Anthropic Claude Code
- [[Codex]] - OpenAI Codex
- [[Aider]] - AI coding assistant
- [[Parallel-Processing]] - 并行处理
- [[Plugin-Architecture]] - 插件架构
- [[CI-Automation]] - CI自动化

---

> 来源: [GitHub](https://github.com/ComposioHQ/agent-orchestrator) | 置信度: 基于 GitHub README
> 👤 **作者**: ComposioHQ
> ⭐ **Stars**: 1.4k
> 🔗 **官网**: [Composio](https://composio.dev/)
> 📜 **许可证**: MIT
> 💬 **社区**: [Discord](https://discord.gg/UZv7JjxbwG)
