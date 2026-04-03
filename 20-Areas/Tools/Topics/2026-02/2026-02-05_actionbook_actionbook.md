---
title: "actionbook/actionbook: Browser Action Engine for AI Agents (1.5k stars)"
github: "https://github.com/actionbook/actionbook"
owner: actionbook
repo: actionbook
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, ai, agent, browser, automation, rust]
pinboard_tags: [ai, agent, browser]
source_used: github-readme-extract
source_url: "https://github.com/actionbook/actionbook"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# actionbook/actionbook: Browser Action Engine for AI Agents

## 一句话概述

Actionbook 是一个浏览器操作引擎，为 AI Agent 提供现代化的网页操作手册，支持虚拟 DOM、SPA 和流媒体组件，实现 10 倍速度提升和并行多标签页操作。

## 项目定位

**目标用户**:
- 需要自动化网页操作的 AI Agent 开发者
- 构建网页自动化工作流的工程师
- 需要大规模并行网页数据收集的团队
- 寻求浏览器自动化替代方案的开发者

**解决的问题**:
- **速度慢**: 传统 Agent 每步都需截图、解析页面，操作缓慢
- **易出错**: 现代网站的虚拟 DOM、SPA 让传统 Agent 难以交互
- **串行限制**: 一次只能处理一个页面，效率低下
- **动态内容**: 下拉菜单、日期选择器等动态组件难以操作

**使用场景**:
- 批量收集网站信息（如投资组合公司标签行）
- 自动化网页测试和操作
- 多站点数据收集和监控
- AI Agent 网页导航和操作

**与同类项目差异**:
- **10 倍速度**: 操作手册直接指导，无需解析猜测
- **高准确性**: 专为虚拟 DOM、SPA、流媒体组件设计
- **并行能力**: 无状态架构支持数十个标签页并发操作
- **系统浏览器**: 使用现有 Chrome/Brave/Edge，无需额外安装

## README 中文简介

**Actionbook** - 为 AI Agent 打造的浏览器操作引擎

Actionbook 提供针对现代网络构建的最新操作手册，让您的 Agent 能够即时操作任何网站。支持单标签页或数十个标签页并发操作。

**没有 Actionbook**:
- 缓慢：Agent 每步都需截图、解析页面，Airbnb 上搜索一个房间需 15 分钟
- 脆弱：不理解虚拟 DOM、流媒体组件，无法与下拉菜单和动态内容交互
- 串行：必须完成一个页面才能开始下一个，检查 30 个公司网站需 30 轮

**使用 Actionbook**:
- 10 倍速度：操作手册直接告知 Agent 该做什么
- 准确：为虚拟 DOM、SPA 和流媒体组件构建
- 并发：无状态架构，并行操作数十个标签页

**安装**:

```bash
# npm 安装
npm install -g @actionbookdev/cli

# 从源码构建
cargo install --git https://github.com/actionbook/actionbook --path packages/cli --locked
```

基于 Rust 的 CLI 使用您现有的系统浏览器（Chrome、Brave、Edge、Arc、Chromium），无需额外安装浏览器。

**快速开始**:

```bash
actionbook browser start

# 打开标签页
actionbook browser open https://stripe.com --session s1
actionbook browser open https://linear.app --session s1
actionbook browser open https://vercel.com --session s1

# 并发操作所有标签页
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 浏览器控制 | 操作 Chrome/Brave/Edge/Ar 等浏览器 | README | 高 |
| 并行操作 | 无状态架构支持多标签页并发 | README | 高 |
| 现代网页支持 | 虚拟 DOM、SPA、流媒体组件兼容 | README | 高 |
| 操作手册 | 预建操作指南，无需解析猜测 | README | 高 |
| Rust CLI | 高性能 Rust 实现 | README | 高 |
| AI Agent 集成 | 专为 AI Agent 设计的接口 | README | 高 |
| 10 倍速度 | 相比传统方法大幅提升效率 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Actionbook 架构                               │
│           (浏览器操作引擎)                                 │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              CLI 层 (Rust)                         │  │
│  │                                                  │  │
│  │   • 命令行界面                                   │  │
│  │   • 浏览器控制                                   │  │
│  │   • 会话管理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              浏览器引擎层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Chrome       │ Brave        │ Edge         ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ Arc          │ Chromium     │ 更多...       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              操作手册层                            │  │
│  │                                                  │  │
│  │   • 网站特定操作指南                             │  │
│  │   • DOM 交互模式                                 │  │
│  │   • 动态内容处理                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              AI Agent 接口层                       │  │
│  │                                                  │  │
│  │   • Agent 技能 (Skills)                          │  │
│  │   • MCP 服务器集成                               │  │
│  │   • 并发控制                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| CLI | `packages/cli/` | Rust CLI 实现 | 核心 |
| 浏览器控制 | `packages/browser/` | 浏览器自动化 | 核心 |
| 操作手册 | `packages/manuals/` | 网站操作指南 | 核心 |
| MCP 服务器 | `packages/mcp/` | MCP 协议集成 | 扩展 |
| 技能 | `skills/` | Agent 技能 | 扩展 |
| 插件 | `.claude-plugin/` | Claude 插件 | 扩展 |

## 运行与开发方式

**安装**:
```bash
# npm 安装
npm install -g @actionbookdev/cli

# 从源码构建
cargo install --git https://github.com/actionbook/actionbook --path packages/cli --locked
```

**快速开始**:
```bash
# 启动浏览器
actionbook browser start

# 打开标签页
actionbook browser open https://stripe.com --session s1
actionbook browser open https://linear.app --session s1
actionbook browser open https://vercel.com --session s1

# 并发操作所有标签页
```

**开发**:
```bash
# 克隆仓库
git clone https://github.com/actionbook/actionbook.git
cd actionbook

# 安装依赖
pnpm install

# 构建
pnpm build

# 运行测试
pnpm test
```

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `browser start` | 启动浏览器 |
| `browser open <url>` | 打开标签页 |
| `browser close` | 关闭浏览器 |
| `session list` | 列出会话 |
| `manual get <site>` | 获取网站操作手册 |

**MCP 服务器**:
支持 Model Context Protocol，可与 Claude 等 AI 助手集成。

## 数据流 / 控制流

```
AI Agent 请求
    ↓
操作手册查找
    ↓
浏览器控制指令
    ↓
Chrome/Brave/Edge 执行
    ↓
多个标签页并发操作
    ↓
结果返回 Agent
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Rust | CLI 实现 | 高 |
| TypeScript | 插件和工具 | 高 |
| pnpm | 包管理 | 高 |
| Chrome DevTools Protocol | 浏览器控制 | 高 |
| MCP | AI 集成 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | 基础文档，快速开始指南 | 中 |
| 上手难度 | 低 | npm 全局安装即可使用 | 低 |
| 架构复杂度 | 中 | 浏览器控制 + 操作手册系统 | 中 |
| 外部依赖 | 中 | 依赖系统浏览器 | 中 |
| Stars | 中 | 1.5k stars | 中 |
| 维护状态 | 高 | 活跃开发，Apache-2.0 许可 | 高 |

**注意事项**:
- 需要系统已安装 Chrome/Brave/Edge 等浏览器
- Rust 版本需要从源码构建
- MCP 服务器功能需要配合 Claude 等 AI 助手使用

## 关联概念

- [[AI-Agent]] - AI 智能体
- [[Browser-Automation]] - 浏览器自动化
- [[Chrome-DevTools-Protocol]] - Chrome 开发者工具协议
- [[MCP]] - Model Context Protocol
- [[Web-Scraping]] - 网页数据收集
- [[Rust]] - Rust 编程语言

---

> 来源: [GitHub](https://github.com/actionbook/actionbook) | 置信度: 基于 GitHub README
> 👤 **作者**: Actionbook 团队
> ⭐ **Stars**: 1.5k
> 🔗 **官网**: 官网链接在 README 中
> 📜 **许可证**: Apache-2.0
