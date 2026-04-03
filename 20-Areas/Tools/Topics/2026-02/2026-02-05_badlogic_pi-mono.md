---
title: "badlogic/pi-mono: AI Agent 工具集 (30.6k stars)"
github: "https://github.com/badlogic/pi-mono"
owner: badlogic
repo: pi-mono
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, ai, agent, monorepo, typescript, llm]
pinboard_tags: [ai, agent, monorepo]
source_used: github-readme-extract
source_url: "https://github.com/badlogic/pi-mono"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# badlogic/pi-mono: AI Agent 工具集

## 一句话概述

pi-mono 是一个构建 AI Agent 和管理 LLM 部署的工具集合，提供统一的多提供商 LLM API 和 Agent 运行时，是 pi coding agent 的基础仓库。

## 项目定位

**目标用户**:
- 构建 AI Agent 的开发者
- 需要管理多 LLM 提供商集成的团队
- 使用 pi coding agent 的用户
- 寻求 Agent 运行时和工具调用框架的工程师

**解决的问题**:
- **LLM 提供商碎片化**: 不同提供商 API 差异大
- **Agent 运行时复杂**: 工具调用和状态管理繁琐
- **代码重复**: 各项目重复实现 LLM 客户端
- **缺乏统一框架**: 没有标准化的 Agent 构建工具

**使用场景**:
- 构建自定义 AI Agent
- 多 LLM 提供商切换
- Agent 工具调用和状态管理
- 基于 pi 生态的 Agent 开发

**与同类项目差异**:
- **统一 LLM API**: 支持 OpenAI、Anthropic、Google 等多提供商
- **Agent 运行时**: 内置工具调用和状态管理
- **pi 生态基础**: pi coding agent 的基础
- **模块化设计**: 独立包可按需使用

## README 中文简介

**pi-mono** - 构建 AI Agent 和管理 LLM 部署的工具

**⚠️ OSS 周末模式**: Issue 追踪器将于 2026年4月13日 周一重新开放。

OSS 周末从 2026年4月2日 周四到 2026年4月13日 周一。在此期间，未经批准的贡献者提交的新 Issue 和 PR 将被自动关闭。批准的贡献者仍可打开紧急 Issue 和 PR，但请仅限于真正紧急的事务。

**当前重点**: 目前专注于内部重构。

**pi.dev 域名由 exe.dev 慷慨捐赠**

**Pi Monorepo**:

寻找 pi coding agent？参见 `packages/coding-agent` 了解安装和使用。

**Packages**:

| 包 | 描述 |
|----|------|
| `@mariozechner/pi-ai` | 统一多提供商 LLM API (OpenAI、Anthropic、Google 等) |
| `@mariozechner/pi-agent-core` | 带工具调用和状态管理的 Agent 运行时 |

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 多提供商 LLM | OpenAI、Anthropic、Google 等 | README | 高 |
| Agent 运行时 | 工具调用 + 状态管理 | README | 高 |
| pi coding agent | 代码 Agent 实现 | README | 高 |
| 统一 API | 跨提供商统一接口 | README | 高 |
| 模块化 | 独立包设计 | README | 高 |
| TypeScript | TypeScript 实现 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              pi-mono 架构                                    │
│           (AI Agent 工具集)                                  │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   • pi coding agent                              │  │
│  │   • 其他 Agent 应用                              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              包层                                  │  │
│  │                                                  │  │
│  │   ┌──────────────────┬──────────────────┐      │  │
│  │   │ @mariozechner/   │ @mariozechner/   │      │  │
│  │   │ pi-ai            │ pi-agent-core    │      │  │
│  │   │ (统一 LLM API)   │ (Agent 运行时)   │      │  │
│  │   ├──────────────────┼──────────────────┤      │  │
│  │   │ OpenAI           │ 工具调用         │      │  │
│  │   │ Anthropic        │ 状态管理         │      │  │
│  │   │ Google           │                  │      │  │
│  │   │ 更多...          │                  │      │  │
│  │   └──────────────────┴──────────────────┘      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              基础设施层                            │  │
│  │                                                  │  │
│  │   • TypeScript                                   │  │
│  │   • 包管理 (npm/pnpm)                            │  │
│  │   • 测试框架                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| pi-ai | `packages/pi-ai/` | 统一 LLM API | 核心 |
| pi-agent-core | `packages/pi-agent-core/` | Agent 运行时 | 核心 |
| coding-agent | `packages/coding-agent/` | pi coding agent | 应用 |

## 运行与开发方式

**安装 pi coding agent**:
```bash
# 参见 packages/coding-agent 文档
npm install -g @mariozechner/pi-coding-agent
```

**使用包**:
```bash
# pi-ai
npm install @mariozechner/pi-ai

# pi-agent-core
npm install @mariozechner/pi-agent-core
```

**开发**:
```bash
# 克隆仓库
git clone https://github.com/badlogic/pi-mono.git
cd pi-mono

# 安装依赖
npm install

# 构建
npm run build

# 测试
npm test
```

## 外部接口

**pi-ai API**:
```typescript
import { createLLM } from '@mariozechner/pi-ai';

const llm = createLLM({
  provider: 'openai',
  model: 'gpt-4'
});
```

**pi-agent-core API**:
```typescript
import { Agent } from '@mariozechner/pi-agent-core';

const agent = new Agent({
  llm,
  tools: [/* ... */]
});
```

## 数据流 / 控制流

```
用户输入
    ↓
Agent Runtime (pi-agent-core)
    ↓
LLM API 调用 (pi-ai)
    ↓
多提供商 (OpenAI/Anthropic/Google)
    ↓
工具调用请求
    ↓
工具执行
    ↓
结果返回
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 | 高 |
| Node.js | 运行时 | 高 |
| npm | 包管理 | 高 |
| OpenAI API | 提供商支持 | 高 |
| Anthropic API | 提供商支持 | 高 |
| Google API | 提供商支持 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 简洁，指向具体包 | 中 |
| 上手难度 | 中 | 需要查看具体包文档 | 中 |
| 架构复杂度 | 中 | Monorepo 架构 | 中 |
| 外部依赖 | 中 | 依赖 LLM 提供商 API | 中 |
| Stars | 高 | 30.6k stars | 高 |
| 维护状态 | 高 | 活跃开发，有 OSS 周末机制 | 高 |

**注意事项**:
- 目前处于 OSS 周末模式（至 2026-04-13）
- 新 Issue 和 PR 可能被自动关闭
- 内部正在重构
- 紧急事务需获得批准

**当前状态**:
- Issue 追踪器关闭至 2026年4月13日
- 专注于内部重构
- 批准贡献者可提交紧急事务

## 关联概念

- [[pi-coding-agent]] - 基于 pi-mono 的代码 Agent
- [[LLM-API]] - 大语言模型 API
- [[Agent-Runtime]] - Agent 运行时
- [[TypeScript]] - TypeScript 编程语言
- [[Monorepo]] - 单仓库多包管理
- [[Tool-Calling]] - 工具调用机制

---

> 来源: [GitHub](https://github.com/badlogic/pi-mono) | 置信度: 基于 GitHub README
> 👤 **作者**: badlogic (Mario Zechner)
> ⭐ **Stars**: 30.6k
> 🔗 **官网**: [pi.dev](https://pi.dev) (由 exe.dev 捐赠)
> 📜 **许可证**: MIT
