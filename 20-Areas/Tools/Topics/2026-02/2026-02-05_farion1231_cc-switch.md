---
title: "farion1231/cc-switch: AI CLI 统一管理工具 (37.7k stars)"
github: "https://github.com/farion1231/cc-switch"
owner: farion1231
repo: cc-switch
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, ai-cli, claude-code, codex, gemini, openclaw, tauri, desktop-app]
pinboard_tags: [ai-tools, cli-manager, desktop-app]
source_used: github-readme-extract
source_url: "https://github.com/farion1231/cc-switch"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# farion1231/cc-switch: AI CLI 统一管理工具

## 一句话概述

CC Switch 是一个跨平台桌面应用，统一管理 Claude Code、Codex、Gemini CLI、OpenCode 和 OpenClaw 五个 AI CLI 工具的配置切换，支持 50+ 供应商预设、统一 MCP/Skills 管理和系统托盘快捷操作，无需手动编辑配置文件。

## 项目定位

**目标用户**:
- 同时使用多个 AI CLI 工具(Claude Code, Codex, Gemini CLI 等)的开发者
- 需要频繁切换 API 供应商或账号的用户
- 希望统一管理 MCP 服务器和 Skills 的开发者
- 对配置管理有可视化需求的用户

**解决的问题**:
- **配置分散**: 每个 CLI 工具有独立的配置格式和位置
- **切换繁琐**: 更换 API 供应商需要手动编辑 JSON/TOML/.env 文件
- **MCP 管理困难**: 不同工具的 MCP 服务器配置无法统一管理
- **缺乏可视化**: 纯命令行配置对用户不够友好
- **多端同步**: 多设备间配置难以保持一致

**使用场景**:
- 一键切换 Claude Code 的 API 供应商
- 统一管理多个 CLI 工具的 MCP 服务器
- 快速在不同 AI 账号间切换
- 跨设备同步配置
- 系统托盘快速切换

**与同类项目差异**:
- **五合一管理**: 同时支持 Claude Code、Codex、Gemini CLI、OpenCode、OpenClaw
- **50+ 供应商预设**: 包含 AWS Bedrock、NVIDIA NIM 和社区中继
- **统一 MCP 管理**: 一个面板管理四个应用的 MCP 服务器
- **系统托盘**: 无需打开主界面即可快速切换
- **云同步**: 支持 Dropbox、OneDrive、iCloud、WebDAV 同步

## README 中文简介

**CC Switch** - Claude Code、Codex、Gemini CLI、OpenCode 和 OpenClaw 的 All-in-One 管理器

**核心功能**:
- **一个应用，五个 CLI 工具**: 统一管理 Claude Code、Codex、Gemini CLI、OpenCode、OpenClaw
- **无需手动编辑配置**: 50+ 供应商预设，一键导入
- **统一 MCP & Skills 管理**: 一个面板管理四个应用的 MCP 服务器和双向同步
- **系统托盘快捷切换**: 点击托盘图标直接切换供应商
- **云同步**: 通过 Dropbox、OneDrive、iCloud 或 WebDAV 跨设备同步

**主要功能模块**:

**供应商管理**:
- 5 个 CLI 工具，50+ 预设
- 通用供应商: 一个配置同步到多个应用
- 一键切换、系统托盘快捷访问
- 拖拽排序、导入/导出

**代理与故障转移**:
- 本地代理热切换: 格式转换、自动故障转移、熔断器
- 应用级代理: 独立代理 Claude、Codex 或 Gemini

**MCP、Prompts & Skills**:
- 统一 MCP 面板: 管理四个应用的 MCP 服务器
- Prompts: Markdown 编辑器，跨应用同步
- Skills: 从 GitHub 仓库或 ZIP 一键安装

**用量与成本追踪**:
- 用量仪表板: 追踪花费、请求和 Token
- 会话管理器: 浏览、搜索、恢复对话历史

**系统与平台**:
- 云同步: 自定义配置目录、WebDAV 服务器同步
- 深度链接 (ccswitch://): 通过 URL 导入供应商、MCP、Prompts、Skills
- 深色/浅色/系统主题、自动启动、自动更新

**快速开始**:

**macOS (Homebrew)**:
```bash
brew tap farion1231/ccswitch
brew install --cask cc-switch
```

**手动下载**:
- Windows: MSI 安装程序或便携版 ZIP
- macOS: DMG 或 ZIP
- Linux: DEB、RPM、AppImage 或 Flatpak

**基本使用**:
1. 点击"添加供应商" → 选择预设或创建自定义配置
2. 切换供应商:
   - 主界面: 选择供应商 → 点击"启用"
   - 系统托盘: 直接点击供应商名称
3. 生效: 重启终端或对应的 CLI 工具(Claude Code 无需重启)

**MCP 使用**:
1. 点击"MCP"按钮
2. 通过模板或自定义配置添加服务器
3. 切换每个应用的同步设置

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 五合一管理 | Claude Code、Codex、Gemini CLI、OpenCode、OpenClaw | README | 高 |
| 50+ 供应商预设 | AWS Bedrock、NVIDIA NIM、社区中继等 | README | 高 |
| 统一 MCP 管理 | 跨四个应用的 MCP 服务器统一管理 | README | 高 |
| 统一 Skills 管理 | GitHub/ZIP 一键安装到所有应用 | README | 高 |
| 系统托盘切换 | 无需打开主界面即可切换供应商 | README | 高 |
| 本地代理 | 格式转换、自动故障转移、熔断器 | README | 高 |
| 云同步 | Dropbox、OneDrive、iCloud、WebDAV | README | 高 |
| 会话管理 | 浏览、搜索、恢复对话历史 | README | 高 |
| 用量追踪 | 花费、请求、Token 趋势图表 | README | 高 |
| 深度链接 | ccswitch:// 协议导入配置 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              CC Switch 架构                                │
│           (AI CLI 统一管理工具)                             │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              前端层 (React + TS)                  │  │
│  │                                                  │  │
│  │   ┌─────────────┐ ┌──────────────┐ ┌──────────┐ │  │
│  │   │ Components  │ │    Hooks     │ │ TanStack │ │  │
│  │   │    (UI)     │ │ (Bus. Logic) │ │  Query   │ │  │
│  │   └─────────────┘ └──────────────┘ └──────────┘ │  │
│  │                                                  │  │
│  │   UI 组件: Providers/MCP/Prompts/Skills/        │  │
│  │   Sessions/Proxy/Settings/Universal             │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼ Tauri IPC                      │
│  ┌─────────────────────────────────────────────────┐  │
│  │              后端层 (Tauri + Rust)                │  │
│  │                                                  │  │
│  │   ┌─────────────┐ ┌──────────────┐ ┌──────────┐ │  │
│  │   │  Commands   │ │   Services   │ │  Models  │ │  │
│  │   │ (API Layer) │ │ (Bus. Layer) │ │ (Data)   │ │  │
│  │   └─────────────┘ └──────────────┘ └──────────┘ │  │
│  │                                                  │  │
│  │   Services:                                     │  │
│  │   • ProviderService (供应商 CRUD/切换/回填)    │  │
│  │   • McpService (MCP 服务器管理/同步)             │  │
│  │   • ProxyService (本地代理/格式转换)             │  │
│  │   • SessionManager (Claude 对话历史)             │  │
│  │   • ConfigService (导入导出/备份)                │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              数据层                                │  │
│  │                                                  │  │
│  │   • SQLite (~/.cc-switch/cc-switch.db)          │  │
│  │   • 本地设置 (~/.cc-switch/settings.json)       │  │
│  │   • 备份 (~/.cc-switch/backups/)                │  │
│  │   • Skills (~/.cc-switch/skills/)               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 前端 UI | `src/` | React + TypeScript 界面 | 用户接口 |
| 供应商管理 | `src/components/providers/` | 供应商 CRUD 和切换 | 核心功能 |
| MCP 面板 | `src/components/mcp/` | MCP 服务器管理 | 核心功能 |
| Skills 管理 | `src/components/skills/` | Skills 安装管理 | 核心功能 |
| 后端命令 | `src-tauri/src/commands/` | Tauri 命令层 | API 层 |
| 业务服务 | `src-tauri/src/services/` | 业务逻辑层 | 核心引擎 |
| 数据库 | `src-tauri/src/database/` | SQLite DAO 层 | 数据层 |

## 运行与开发方式

**环境要求**:
- Node.js 18+
- pnpm 8+
- Rust 1.85+
- Tauri CLI 2.8+

**开发命令**:
```bash
# 安装依赖
pnpm install

# 开发模式(热重载)
pnpm dev

# 类型检查
pnpm typecheck

# 格式化代码
pnpm format

# 运行单元测试
pnpm test:unit

# 构建应用
pnpm build
```

**Rust 后端开发**:
```bash
cd src-tauri

# 格式化代码
cargo fmt

# 运行 clippy 检查
cargo clippy

# 运行后端测试
cargo test
```

**测试**:
- 前端: vitest + MSW + @testing-library/react
- 后端: cargo test

## 外部接口

**CLI 工具支持**:
| 工具 | 配置管理 | MCP 管理 | Skills 管理 |
|------|----------|----------|-------------|
| Claude Code | ✅ | ✅ | ✅ |
| Codex | ✅ | ✅ | ✅ |
| Gemini CLI | ✅ | ✅ | ✅ |
| OpenCode | ✅ | ✅ | ✅ |
| OpenClaw | ✅ | ✅ | ✅ |

**深度链接协议**:
| 操作 | URL 格式 |
|------|----------|
| 导入供应商 | `ccswitch://provider/...` |
| 导入 MCP | `ccswitch://mcp/...` |
| 导入 Prompts | `ccswitch://prompt/...` |
| 导入 Skills | `ccswitch://skill/...` |

**数据存储**:
| 文件 | 路径 | 内容 |
|------|------|------|
| 数据库 | `~/.cc-switch/cc-switch.db` | SQLite - 供应商、MCP、Prompts、Skills |
| 设置 | `~/.cc-switch/settings.json` | 设备级 UI 偏好 |
| 备份 | `~/.cc-switch/backups/` | 自动轮转，保留最近 10 个 |
| Skills | `~/.cc-switch/skills/` | 默认符号链接到对应应用 |

## 数据流 / 控制流

```
用户操作 (添加/切换供应商)
    ↓
前端 React 组件
    ↓
TanStack Query 缓存/同步
    ↓
Tauri IPC 调用
    ↓
Rust Commands 层
    ↓
Services 业务逻辑
    ↓
SQLite 数据库操作
    ↓
写回 CLI 工具配置文件
    ↓
生效 (部分工具需重启)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| React 18 | 前端框架 | 高 |
| TypeScript | 类型系统 | 高 |
| Tauri 2.8 | 跨平台桌面框架 | 高 |
| Rust | 后端语言 | 高 |
| Vite | 构建工具 | 高 |
| TailwindCSS | UI 样式 | 高 |
| TanStack Query | 数据缓存/同步 | 高 |
| SQLite | 本地数据库 | 高 |
| vitest | 测试框架 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细 README、用户手册 | 高 |
| 上手难度 | 低 | 图形界面，一键操作 | 低 |
| 架构复杂度 | 中 | 前端+后端+数据库 | 中 |
| 外部依赖 | 低 | 本地运行，数据自持 | 低 |
| Stars | 高 | 37.7k stars | 高 |
| 维护状态 | 高 | 活跃开发，35 个 releases | 高 |

**注意事项**:
- 部分 CLI 工具切换后需要重启才能生效(Claude Code 除外)
- macOS 版本已签名和公证
- 云同步需要用户自行配置云存储
- 供应商配置涉及 API key，注意保护隐私

## 关联概念

- [[Claude-Code]] - Anthropic CLI 编码工具
- [[Codex]] - OpenAI 代码生成模型
- [[Gemini-CLI]] - Google Gemini 命令行工具
- [[OpenClaw]] - 开源 AI Agent 框架
- [[MCP]] - Model Context Protocol
- [[Tauri]] - Rust + Web 跨平台框架
- [[AI-CLI-Tools]] - AI 命令行工具生态

---

> 来源: [GitHub](https://github.com/farion1231/cc-switch) | 置信度: 基于 GitHub README
> 👤 **作者**: farion1231 (Jason Young)
> ⭐ **Stars**: 37.7k
> 📜 **许可证**: MIT
