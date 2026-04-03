---
title: "psiace/bub: 群聊友好的 Agent 框架 (1 star)"
github: "https://github.com/psiace/bub"
owner: psiace
repo: bub
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, python, agent, chat, hook, plugin]
pinboard_tags: [python, agent, chat]
source_used: github-readme-extract
source_url: "https://github.com/psiace/bub"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# psiace/bub: 群聊友好的 Agent 框架

## 一句话概述

bub 是一个为与人类和其他 Agent 在群聊中 coexist 设计的 Agent 框架，hook-first 架构基于 pluggy，核心仅 ~200 行，支持 CLI、Telegram 等多渠道。

## 项目定位

**目标用户**:
- 需要群聊集成的 Agent 开发者
- 寻求轻量级 Agent 框架的工程师
- 希望多平台部署 Agent 的团队
- 喜欢插件化架构的开发者

**解决的问题**:
- **群聊复杂性**: Agent 需要在并发任务、不完整上下文中工作
- **框架臃肿**: 现有框架过于复杂，学习成本高
- **渠道限制**: 多数 Agent 只支持单一渠道
- **状态管理**: 会话累积模式不适合群聊场景
- **扩展困难**: 难以自定义和扩展功能

**使用场景**:
- 群聊助手（微信群、Telegram 群）
- 多人协作 Agent
- 跨平台 Agent 部署
- 可插拔功能扩展

**与同类项目差异**:
- **群聊优先**: 专为与人类和其他 Agent coexist 设计
- **hook-first**: 基于 pluggy 的钩子架构
- **极小核心**: 仅 ~200 行核心代码
- **Tape 上下文**: 使用 tape 而非会话累积管理上下文
- **内置即插件**: builtins 只是默认插件，可替换

## README 中文简介

**bub** - 与人共存的 Agent 通用形态

**起源**:

bub 始于群聊。不是作为演示或个人助手，而是作为必须与人类和其他 Agent 在同一混乱对话中共存的队友 —— 并发任务、不完整上下文，没人等待。

**架构**:

- **Hook-first**: 基于 pluggy 构建
- **极小核心**: ~200 行
- **内置即插件**: builtins 只是可替换的默认插件
- **Tape 上下文**: 使用 tape 而非会话累积管理上下文
- **统一管道**: 同一管道跨 CLI、Telegram 和你添加的任何渠道运行

**快速开始**:

**pip 安装**:
```bash
pip install bub
```

**从源码**:
```bash
git clone https://github.com/bubbuild/bub.git
cd bub
uv sync
uv run bub chat                         # 交互式会话
uv run bub run "summarize this repo"    # 一次性任务
uv run bub gateway                      # 渠道监听模式
```

**工作原理**:

每条入站消息通过单一 turn pipeline。每个阶段都是 hook：

```
resolve_session → load_state → build_prompt → run_model
                                                ↓
dispatch_outbound ← render_outbound ← save_state
```

**Builtins 是插件**:

先注册 builtins，然后是其他插件。后面的插件覆盖前面的。无特殊情况。

**AGENTS.md 集成**:

如果工作区存在 `AGENTS.md`，它会自动附加到系统提示。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Hook-first | 基于 pluggy 的钩子架构 | README | 高 |
| 极小核心 | ~200 行核心代码 | README | 高 |
| 插件系统 | builtins 可替换 | README | 高 |
| Tape 上下文 | tape 而非会话累积 | README | 高 |
| 多渠道 | CLI、Telegram、Gateway | README | 高 |
| AGENTS.md | 自动附加到系统提示 | README | 高 |
| 群聊友好 | 专为多 Agent 场景设计 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              bub 架构                                        │
│           (群聊友好 Agent 框架)                              │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              渠道层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ CLI          │ Telegram     │ Gateway      ││  │
│  │   │ (命令行)     │ (电报)       │ (API)        ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Turn Pipeline                       │  │
│  │                                                  │  │
│  │   resolve_session → load_state → build_prompt   │  │
│  │                         ↓                        │  │
│  │                     run_model                    │  │
│  │                         ↓                        │  │
│  │   save_state → render_outbound → dispatch_outbound│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Hook 层 (pluggy)                      │  │
│  │                                                  │  │
│  │   • builtins (默认插件)                          │  │
│  │   • 自定义插件 (覆盖 builtins)                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心层 (~200 行)                      │  │
│  │                                                  │  │
│  │   • Tape 上下文管理                              │  │
│  │   • 插件注册                                     │  │
│  │   • Pipeline 执行                                │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心 | `src/bub/` | ~200 行核心 | 核心 |
| 源码 | `src/` | 源代码 | 核心 |
| 测试 | `tests/` | 测试套件 | 质量 |
| 文档 | `docs/` | 文档 | 文档 |

## 运行与开发方式

**pip 安装**:
```bash
pip install bub
```

**从源码**:
```bash
git clone https://github.com/bubbuild/bub.git
cd bub
uv sync
```

**运行**:
```bash
# 交互式会话
uv run bub chat

# 一次性任务
uv run bub run "summarize this repo"

# 渠道监听模式
uv run bub gateway
```

**开发插件**:
```python
# 使用 pluggy 开发自定义 hook
import pluggy

hookspec = pluggy.HookspecMarker("bub")
hookimpl = pluggy.HookimplMarker("bub")
```

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `bub chat` | 交互式会话 |
| `bub run <task>` | 一次性任务 |
| `bub gateway` | 渠道监听模式 |

**Hook 点**:
| Hook | 阶段 |
|------|------|
| `resolve_session` | 解析会话 |
| `load_state` | 加载状态 |
| `build_prompt` | 构建提示 |
| `run_model` | 运行模型 |
| `save_state` | 保存状态 |
| `render_outbound` | 渲染输出 |
| `dispatch_outbound` | 分发输出 |

## 数据流 / 控制流

```
入站消息
    ↓
resolve_session → 确定会话
    ↓
load_state → 从 tape 加载上下文
    ↓
build_prompt → 构建提示（含 AGENTS.md）
    ↓
run_model → LLM 调用
    ↓
save_state → 保存到 tape
    ↓
render_outbound → 渲染响应
    ↓
dispatch_outbound → 发送回渠道
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| pluggy | Hook 系统 | 高 |
| uv | 包管理 | 高 |
| Docker | 容器化 | 中 |
| MkDocs | 文档 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 清晰 | 中 |
| 上手难度 | 低 | pip 安装，uv 开发 | 低 |
| 架构复杂度 | 低 | ~200 行核心 | 低 |
| 外部依赖 | 低 | 依赖少 | 低 |
| Stars | 低 | 1 star (fork) | 低 |
| 维护状态 | 中 | 新架构 | 中 |

**注意事项**:
- 是 fork 项目，非原创
- 架构较新，生态待发展
- 需要理解 pluggy hook 系统

**设计哲学**:
- 群聊优先
- 简单可维护
- 可插拔扩展

## 关联概念

- [[pluggy]] - Python 插件系统
- [[Hook-System]] - 钩子架构
- [[Agent-Framework]] - Agent 框架
- [[Group-Chat]] - 群聊 Agent
- [[Telegram-Bot]] - Telegram 机器人
- [[Tape-Context]] - Tape 上下文管理

---

> 来源: [GitHub](https://github.com/psiace/bub) | 置信度: 基于 GitHub README
> 👤 **作者**: psiace (forked from bubbuild/bub)
> ⭐ **Stars**: 1
> 🔗 **官网**: [GitHub](https://github.com/psiace/bub)
> 📜 **许可证**: 未明确
