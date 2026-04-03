---
title: "netease-youdao/lobsterai: 网易有道全能个人助理Agent (4.8k stars)"
github: "https://github.com/netease-youdao/lobsterai"
owner: netease-youdao
repo: lobsterai
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, typescript, electron, ai, agent, productivity, opencode]
pinboard_tags: [ai, agent, productivity]
source_used: github-readme-extract
source_url: "https://github.com/netease-youdao/lobsterai"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# netease-youdao/lobsterai: 网易有道全能个人助理Agent

## 一句话概述

LobsterAI是网易有道开发的24/7全能个人助理Agent，基于Electron和Claude Agent SDK构建，支持本地/沙箱执行、16+内置技能、IM远程控制、持久记忆和定时任务。

## 项目定位

**目标用户**:
- 需要AI个人助理的知识工作者
- 希望自动化日常任务的开发者
- 需要远程控制AI的手机用户
- 寻求安全AI执行环境的团队

**解决的问题**:
- **AI工具碎片化**: 不同任务需要不同AI工具
- **执行环境不安全**: AI直接操作系统存在风险
- **移动端缺失**: 桌面AI无法在手机上使用
- **上下文遗忘**: 每次对话都从零开始
- **重复任务**: 周期性任务需要手动触发

**使用场景**:
- 数据分析和报表生成
- PPT和文档自动创建
- 视频内容生成
- 网页搜索和信息收集
- 邮件自动处理
- 定时任务自动化

**与同类项目差异**:
- **Cowork模式**: 本地+沙箱双模式执行，所有操作需用户审批
- **IM集成**: 支持Telegram、Discord、钉钉、飞书远程控制
- **16+内置技能**: 文档生成、视频制作、网页自动化等
- **持久记忆**: 自动提取用户偏好，跨会话保持
- **Windows内置Python**: 打包Python运行时，无需用户安装

## README 中文简介

**LobsterAI** — 7×24小时全能个人助理Agent

网易有道开发的全能个人助理Agent，全天候处理日常任务：数据分析、制作演示文稿、生成视频、撰写文档、搜索网页、发送邮件、定时任务等。

**核心特性**:
- **Cowork模式**: 在本地或沙箱环境中执行工具、操作文件、运行命令
- **16+内置技能**: Office文档生成、网页搜索、Playwright自动化、Remotion视频生成等
- **IM远程控制**: 通过Telegram、Discord、钉钉、飞书从手机远程触发Agent
- **持久记忆**: 自动提取用户偏好和个人信息，越用越智能
- **权限门控**: 所有工具调用需显式用户审批
- **定时任务**: 支持Cron表达式，自动生成周期性报告

**执行模式**:
| 模式 | 说明 |
|------|------|
| auto | 根据上下文自动选择 |
| local | 直接本地执行，全速运行 |

**架构**:
- Electron严格进程隔离
- 主进程: 窗口管理、SQLite持久化、CoworkRunner、IM网关
- 渲染进程: React 18 + Redux Toolkit + Tailwind CSS
- IPC通信: 40+通道，类型检查

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Cowork系统 | 基于Claude Agent SDK的AI工作会话 | README | 高 |
| 本地执行 | 直接本地环境运行 | README | 高 |
| 沙箱执行 | OpenClaw沙箱隔离执行 | README | 高 |
| 权限门控 | 工具调用需用户审批 | README | 高 |
| IM集成 | Telegram/Discord/钉钉/飞书 | README | 高 |
| 持久记忆 | 自动提取用户偏好 | README | 高 |
| 定时任务 | Cron调度系统 | README | 高 |
| 16+技能 | 文档/视频/搜索/邮件等 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              LobsterAI 架构                                │
│           (全能个人助理Agent)                               │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              界面层 (React 18)                   │  │
│  │                                                  │  │
│  │   • Electron窗口管理                             │  │
│  │   • Redux状态管理                                │  │
│  │   • Tailwind CSS样式                             │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              主进程层 (Electron)                   │  │
│  │                                                  │  │
│  │   • CoworkRunner (Agent SDK执行)                │  │
│  │   • SQLite持久化                                 │  │
│  │   • IM网关 (Telegram/Discord/钉钉/飞书)          │  │
│  │   • 技能管理器                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心引擎层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Cowork系统   │ 记忆提取器   │ 定时任务    ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ 技能系统     │ IM网关       │ 权限控制    ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              执行环境层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ 本地执行     │ 沙箱执行     │              │  │
│  │   │ (直接)       │ (OpenClaw)   │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 主进程 | `src/main/` | Electron主进程、IPC、存储 | 核心 |
| 渲染进程 | `src/renderer/` | React UI、状态管理 | 核心 |
| 技能定义 | `SKILLs/` | 16+技能配置和实现 | 核心 |
| OpenClaw扩展 | `openclaw-extensions/` | 沙箱扩展 | 扩展 |
| 构建脚本 | `scripts/` | 打包和分发脚本 | 工具 |
| 测试 | `tests/` | 测试套件 | 质量 |

## 运行与开发方式

**环境要求**:
- Node.js >= 24 < 25
- npm

**开发**:
```bash
git clone https://github.com/netease-youdao/LobsterAI.git
cd lobsterai
npm install
npm run electron:dev
```

**OpenClaw开发模式**:
```bash
# 首次运行：自动克隆构建OpenClaw
npm run electron:dev:openclaw

# 强制重建
OPENCLAW_FORCE_BUILD=1 npm run electron:dev:openclaw
```

**打包分发**:
```bash
# macOS (.dmg)
npm run dist:mac

# Windows (.exe)
npm run dist:win

# Linux (.AppImage & .deb)
npm run dist:linux
```

**Windows Python运行时**:
Windows构建自动打包Python运行时到 `resources/python-win`

## 外部接口

**IM集成**:
| 平台 | 协议 | 说明 |
|------|------|------|
| 钉钉 | DingTalk Stream | 企业机器人双向通信 |
| 飞书 | Lark SDK | 飞书应用机器人 |
| Telegram | grammY | Bot API集成 |
| Discord | discord.js | Discord bot集成 |
| 网易IM | node-nim V2 | 网易IM P2P消息 |

**内置技能**:
| 技能 | 功能 | 典型场景 |
|------|------|----------|
| web-search | 网页搜索 | 信息检索、研究 |
| docx | Word文档生成 | 报告、提案 |
| xlsx | Excel表格生成 | 数据分析、仪表盘 |
| pptx | PPT创建 | 演示、业务汇报 |
| pdf | PDF处理 | 文档解析、格式转换 |
| remotion | 视频生成 | 宣传视频、数据可视化动画 |
| playwright | 网页自动化 | 浏览器任务、自动化测试 |
| scheduled-task | 定时任务 | 周期性自动化工作流 |
| imap-smtp-email | 邮件收发 | 邮件处理、自动回复 |

**Cowork配置**:
- Working Directory: Agent操作根目录
- System Prompt: 自定义Agent行为
- Execution Mode: auto / local

**记忆设置**:
| 设置 | 说明 | 默认 |
|------|------|------|
| Memory Toggle | 启用/禁用记忆 | On |
| Auto Capture | 自动提取记忆 | On |
| Capture Strictness | 提取敏感度 | Standard |
| Max Injected Items | 每会话注入记忆数 | 12 |

## 数据流 / 控制流

```
用户输入 (桌面UI / IM消息)
    ↓
Cowork会话创建
    ↓
Agent推理和工具选择
    ↓
权限请求 (需用户审批)
    ↓
工具执行 (本地/沙箱)
    ↓
记忆提取和存储
    ↓
结果返回用户
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (73.6%) | 高 |
| Electron 40 | 框架 | 高 |
| React 18 | UI框架 | 高 |
| Redux Toolkit | 状态管理 | 高 |
| Tailwind CSS | 样式 | 高 |
| Vite 5 | 构建 | 高 |
| Claude Agent SDK | AI引擎 | 高 |
| SQLite | 存储 | 高 |
| OpenClaw | 沙箱执行 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，中英双语 | 高 |
| 上手难度 | 中 | 需要Node.js环境 | 中 |
| 架构复杂度 | 高 | Electron + AI + 多IM集成 | 高 |
| 外部依赖 | 中 | 需要Claude API | 中 |
| Stars | 高 | 4.8k stars | 高 |
| 维护状态 | 高 | 网易有道官方维护 | 高 |

**注意事项**:
- 所有工具调用需用户显式审批
- 文件操作限制在指定工作目录
- 支持context isolation和sandbox
- Windows内置Python运行时

**安全模型**:
- 进程隔离: Context isolation启用，node integration禁用
- 权限门控: 工具调用需用户审批
- 沙箱执行: 可选OpenClaw沙箱
- 工作区边界: 文件操作限制在工作目录
- IPC验证: 所有跨进程调用类型检查

## 关联概念

- [[Claude-Agent-SDK]] - Anthropic Agent SDK
- [[Electron]] - 跨平台桌面应用框架
- [[OpenClaw]] - 沙箱执行环境
- [[React-18]] - UI框架
- [[Redux-Toolkit]] - 状态管理
- [[Tailwind-CSS]] - CSS框架
- [[Vite]] - 构建工具
- [[SQLite]] - 嵌入式数据库
- [[Telegram-Bot]] - Telegram机器人
- [[DingTalk]] - 钉钉开放平台
- [[Lark]] - 飞书开放平台

---

> 来源: [GitHub](https://github.com/netease-youdao/lobsterai) | 置信度: 基于 GitHub README
> 👤 **作者**: NetEase Youdao (网易有道)
> ⭐ **Stars**: 4.8k
> 🔗 **官网**: [lobsterai.youdao.com](https://lobsterai.youdao.com)
> 📜 **许可证**: MIT
