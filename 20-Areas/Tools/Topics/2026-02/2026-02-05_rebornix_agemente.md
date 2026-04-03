---
title: "rebornix/Agmente: iOS Agent 客户端 (492 stars)"
github: "https://github.com/rebornix/Agmente"
owner: rebornix
repo: Agmente
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, ios, agent, acp, client, swift]
pinboard_tags: [ios, agent, client]
source_used: github-readme-extract
source_url: "https://github.com/rebornix/Agmente"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# rebornix/Agmente: iOS Agent 客户端

## 一句话概述

Agmente 是一个 iOS 平台的 AI Agent 客户端，支持 ACP (Agent Client Protocol) 和 Codex app-server 协议，可在设备上查看工具调用、结果和对话历史，支持远程 Agent 连接。

## 项目定位

**目标用户**:
- 需要在 iOS 设备上使用 AI Agent 的开发者
- 希望通过移动设备监控 Agent 执行的用户
- 需要远程连接 Agent 服务器的团队

**解决的问题**:
- **移动端 Agent 交互**: 在 iOS 设备上查看 Agent 执行状态
- **远程 Agent 监控**: 连接远程服务器上的 ACP 或 Codex Agent
- **工具调用可视化**: 查看工具调用和结果记录
- **安全防护**: 支持 Cloudflare Tunnel + Access 凭证保护

**使用场景**:
- 移动端监控 AI Agent 执行
- 远程开发环境 Agent 管理
- 随时随地查看 Agent 对话历史
- 团队共享 Agent 会话监控

**与同类项目差异**:
- **多协议支持**: 同时支持 ACP 和 Codex app-server 协议
- **iOS 原生**: 专为 iOS 设备优化的原生体验
- **远程连接**: 支持 wss:// 远程 Agent 连接
- **安全集成**: Cloudflare Access 服务令牌支持

## README 中文简介

**Agmente** - iOS 平台的 Coding Agent 客户端

Agmente 连接支持 ACP (Agent Client Protocol) 或 Codex app-server 协议的服务器，在设备上显示工具调用、结果和对话历史。

**下载**: App Store 搜索 "Agmente"

**核心能力**:
- 连接 ACP Agent（Copilot CLI、Gemini CLI、Claude Code 适配器、Qwen、Mistral Vibe 等）
- 连接 Codex app-server 端点
- 在对话记录中查看工具调用和结果
- 可选的 Cloudflare Tunnel + Access 凭证用于远程访问

**远程 Agent**:

在远程主机启动 ACP 或 Codex app-server Agent，并通过 wss:// 暴露。

当端点受保护时使用 bearer tokens 和/或 Cloudflare Access 服务令牌。

完整设置参见 setup.md，快速开始：

```bash
# 在远程主机运行（启动/停止为独立命令）
npx -y @rebornix/stdio-to-ws --persist --grace-period 604800 "copilot --acp" --port 8765
pkill -9 -f "stdio-to-ws.*8765"
```

暴露端口 behind TLS，然后使用 wss://<your-host> 从 Agmente 连接。

**仓库结构**:
- `Agmente/` - iOS 应用源码
- `ACPClient/` - 应用使用的 Swift 包
- `AppServerClient/` - Codex app-server 客户端支持

**构建要求**:
- Xcode（推荐最新稳定版）
- macOS 用于 iOS 构建

**构建 (iOS)**:

在 Xcode 中打开 `Agmente.xcodeproj`，在模拟器或设备上运行 Agmente scheme。

CLI 构建示例:
```bash
xcodebuild -project Agmente.xcodeproj -scheme Agmente -destination 'platform=iOS Simulator,name=iPhone 16'
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| ACP 协议 | Agent Client Protocol 支持 | README | 高 |
| Codex 协议 | Codex app-server 协议支持 | README | 高 |
| iOS 原生 | Swift 原生 iOS 应用 | README | 高 |
| 远程连接 | 通过 wss:// 连接远程 Agent | README | 高 |
| 工具调用可视化 | 查看工具调用和结果 | README | 高 |
| Cloudflare 集成 | Tunnel + Access 安全支持 | README | 高 |
| 多 Agent 支持 | Copilot、Gemini、Claude 等 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Agmente 架构                                  │
│           (iOS Agent 客户端)                                │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              iOS 应用层                            │  │
│  │                                                  │  │
│  │   • 对话界面                                     │  │
│  │   • 工具调用显示                                 │  │
│  │   • 历史记录查看                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              客户端库层                            │  │
│  │                                                  │  │
│  │   ┌──────────────────┬──────────────────┐      │  │
│  │   │ ACPClient        │ AppServerClient  │      │  │
│  │   │ (ACP 协议)        │ (Codex 协议)      │      │  │
│  │   └──────────────────┴──────────────────┘      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              网络连接层                            │  │
│  │                                                  │  │
│  │   • WebSocket (wss://)                           │  │
│  │   • Bearer Token 认证                            │  │
│  │   • Cloudflare Access                            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| iOS 应用 | `Agmente/` | iOS 应用源码 | 核心 |
| ACP 客户端 | `ACPClient/` | ACP 协议实现 | 核心 |
| Codex 客户端 | `AppServerClient/` | Codex 协议支持 | 核心 |
| Agent 技能 | `.agents/skills/` | Agent 技能定义 | 扩展 |
| MCP | `.xcodebuildmcp/` | MCP 服务器 | 扩展 |

## 运行与开发方式

**安装**:
App Store 搜索 "Agmente" 下载安装

**开发**:
```bash
# 克隆仓库
git clone https://github.com/rebornix/Agmente.git
cd Agmente

# 打开 Xcode 项目
open Agmente.xcodeproj

# 或 CLI 构建
xcodebuild -project Agmente.xcodeproj -scheme Agmente -destination 'platform=iOS Simulator,name=iPhone 16'
```

**测试**:
```bash
# 应用测试
xcodebuild -project Agmente.xcodeproj \
  -scheme Agmente \
  -destination "platform=iOS Simulator,id=<SIMULATOR_UDID>" \
  test

# ACPClient 包测试
swift test --package-path ACPClient
```

**远程 Agent 设置**:
```bash
# 启动 stdio-to-ws 桥接
npx -y @rebornix/stdio-to-ws --persist --grace-period 604800 "copilot --acp" --port 8765

# 停止
pkill -9 -f "stdio-to-ws.*8765"
```

## 外部接口

**支持的 Agent**:
| Agent | 协议 |
|-------|------|
| Copilot CLI | ACP |
| Gemini CLI | ACP |
| Claude Code | ACP (适配器) |
| Qwen | ACP |
| Mistral Vibe | ACP |
| OpenAI Codex | Codex app-server |

**远程连接配置**:
- 协议: wss:// (WebSocket Secure)
- 认证: Bearer Token / Cloudflare Access Service Token

## 数据流 / 控制流

```
远程 Agent (stdio-to-ws)
    ↓
WebSocket (wss://)
    ↓
Cloudflare Tunnel (可选)
    ↓
Agmente iOS App
    ↓
ACPClient / AppServerClient
    ↓
UI 显示 (工具调用、结果、对话)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Swift | iOS 开发 | 高 |
| SwiftUI/UIKit | iOS UI | 高 |
| WebSocket | 实时通信 | 高 |
| ACP | Agent 协议 | 高 |
| Cloudflare | 远程访问 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | 基础 README，有 setup.md | 中 |
| 上手难度 | 中 | 需要 Xcode 和 iOS 开发环境 | 中 |
| 架构复杂度 | 中 | iOS 应用 + 协议客户端 | 中 |
| 外部依赖 | 中 | 依赖远程 Agent 服务器 | 中 |
| Stars | 低 | 492 stars | 低 |
| 维护状态 | 中 | 活跃开发，MIT 许可 | 中 |

**注意事项**:
- 需要 iOS 设备或模拟器
- 远程 Agent 需要单独配置
- 部分功能需要 Cloudflare 账户
- App Store 版本可能滞后于源码

## 关联概念

- [[ACP]] - Agent Client Protocol
- [[Codex]] - OpenAI Codex
- [[iOS-Development]] - iOS 开发
- [[Swift]] - Swift 编程语言
- [[WebSocket]] - WebSocket 通信
- [[Cloudflare-Access]] - Cloudflare 访问控制

---

> 来源: [GitHub](https://github.com/rebornix/Agmente) | 置信度: 基于 GitHub README
> 👤 **作者**: rebornix (Peng Lv)
> ⭐ **Stars**: 492
> 🔗 **下载**: [App Store](https://apps.apple.com)
> 📜 **许可证**: MIT
