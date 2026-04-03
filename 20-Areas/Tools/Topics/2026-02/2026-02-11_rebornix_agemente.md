---
title: "rebornix/agmente: iOS Coding Agent客户端 (92 stars)"
github: "https://github.com/rebornix/agmente"
owner: rebornix
repo: agmente
date: 2026-02-11
batch_date: 2026-02-11
type: github-project
tags: [github, ios, swift, agent, acp, codex, mobile]
pinboard_tags: [ai, skill]
source_used: github-readme-extract
source_url: "https://github.com/rebornix/agemente"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# rebornix/agemente: iOS Coding Agent客户端

## 一句话概述

iOS平台的Coding Agent客户端，支持ACP（Agent Client Protocol）和Codex app-server协议，在移动设备上查看工具调用、结果和对话历史。

## 项目定位

**目标用户**:
- 需要在移动设备上使用AI coding agent的开发者
- 希望远程监控AI agent工作的用户
- 使用ACP或Codex协议的开发者
- 寻求移动端AI开发工具的用户

**解决的问题**:
- **移动端AI开发**: 没有原生的iOS coding agent客户端
- **远程监控**: 无法在外出时查看AI agent工作状态
- **协议兼容性**: 需要同时支持多种agent协议
- **安全性**: 需要安全的远程访问方式

**使用场景**:
- 外出时监控AI agent工作
- 移动端查看工具调用和结果
- 远程AC P agent管理
- 多agent切换和监控

**与同类项目差异**:
- **原生iOS**: 专为iOS设计的原生应用
- **多协议支持**: 同时支持ACP和Codex app-server
- **远程友好**: 支持Cloudflare Tunnel远程访问
- **实时展示**: 实时显示工具调用和结果

## README 中文简介

**Agmente** — iOS Coding Agent客户端

连接支持ACP（Agent Client Protocol）或Codex app-server协议的服务器，在设备上显示工具调用、结果和对话历史。

**核心功能**:
- 连接ACP agents（Copilot CLI, Gemini CLI, Claude Code适配器, Qwen, Mistral Vibe等）
- 连接Codex app-server端点
- 在对话中查看工具调用和结果
- 支持Cloudflare Tunnel + Access凭证进行远程访问

**远程Agent设置**:
在远程主机上启动ACP或Codex app-server agent，通过`wss://`暴露，使用bearer tokens或Cloudflare Access服务令牌保护端点。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| ACP协议 | 支持Agent Client Protocol | README | 高 |
| Codex支持 | 支持Codex app-server协议 | README | 高 |
| 多Agent兼容 | Copilot, Gemini, Claude, Qwen, Mistral等 | README | 高 |
| 工具调用展示 | 实时显示工具调用和结果 | README | 高 |
| 远程访问 | Cloudflare Tunnel支持 | README | 高 |
| 安全连接 | Bearer token和Access凭证 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Agmente 架构                                    │
│           (iOS Coding Agent客户端)                           │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              客户端层 (iOS App)                      │  │
│  │                                                  │  │
│  │   • SwiftUI界面                                  │  │
│  │   • 对话展示                                     │  │
│  │   • 工具调用可视化                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              协议层                                  │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ ACPClient    │ AppServer    │              │  │
│  │   │ (ACP协议)    │ (Codex协议)  │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              连接层                                  │  │
│  │                                                  │  │
│  │   • WebSocket (wss://)                           │  │
│  │   • Cloudflare Tunnel                            │  │
│  │   • Bearer Token认证                             │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| iOS App | `Agmente/` | 主应用源码 | 核心 |
| ACP客户端 | `ACPClient/` | ACP协议Swift包 | 核心 |
| AppServer客户端 | `AppServerClient/` | Codex协议支持 | 核心 |
| 远程连接 | `docs/remote-agent.md` | 远程设置文档 | 文档 |

## 运行与开发方式

**下载**:
- [App Store](https://apps.apple.com/us/app/agmente/id6756249477)

**远程Agent快速启动**:
```bash
# 在远程主机上运行
npx -y @rebornix/stdio-to-ws --persist --grace-period 604800 "copilot --acp" --port 8765

# 停止服务
pkill -9 -f "stdio-to-ws.*8765"
```

**构建**:
```bash
# 使用Xcode构建
xcodebuild -project Agmente.xcodeproj -scheme Agmente -destination 'platform=iOS Simulator,name=iPhone 16'
```

**测试**:
```bash
# 应用测试
xcodebuild -project Agmente.xcodeproj -scheme Agmente -destination "platform=iOS Simulator,id=<SIMULATOR_UDID>" test

# ACPClient包测试
swift test --package-path ACPClient
```

## 外部接口

**支持的Agent类型**:
| Agent | 协议 | 状态 |
|-------|------|------|
| Copilot CLI | ACP | 支持 |
| Gemini CLI | ACP | 支持 |
| Claude Code | ACP (适配器) | 支持 |
| Qwen | ACP | 支持 |
| Mistral Vibe | ACP | 支持 |
| Codex | app-server | 支持 |

**连接配置**:
- URL: `wss://<your-host>`
- 认证: Bearer Token / Cloudflare Access

## 数据流 / 控制流

```
远程Agent主机
    ↓
stdio-to-ws桥接 (WebSocket)
    ↓
Cloudflare Tunnel (可选)
    ↓
Agmente iOS App
    ↓
工具调用展示 ← 对话历史 ← 结果展示
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Swift | iOS开发 | 高 |
| SwiftUI | 界面框架 | 高 |
| WebSocket | 实时通信 | 高 |
| ACP协议 | Agent通信标准 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README简洁，有setup文档 | 中 |
| 上手难度 | 低 | App Store直接下载 | 低 |
| 架构复杂度 | 中 | 多协议支持 | 中 |
| 外部依赖 | 中 | 需要远程agent | 中 |
| Stars | 低 | 92 stars | 低 |
| 维护状态 | 中 | 个人项目 | 中 |

**注意事项**:
- 需要远程agent支持WebSocket
- Cloudflare Tunnel设置需要额外配置
- iOS应用需要Xcode构建（如从源码安装）

## 关联概念

- [[ACP]] - Agent Client Protocol
- [[Codex]] - OpenAI Codex
- [[iOS-Development]] - iOS应用开发
- [[SwiftUI]] - SwiftUI界面框架
- [[WebSocket]] - WebSocket实时通信
- [[Cloudflare-Tunnel]] - Cloudflare隧道服务
- [[Remote-Agent]] - 远程Agent模式

---

> 来源: [GitHub](https://github.com/rebornix/agemente) | 置信度: 基于 GitHub README
> 👤 **作者**: rebornix (Peng Lv)
> ⭐ **Stars**: 92
> 🔗 **下载**: [App Store](https://apps.apple.com/us/app/agmente/id6756249477)
> 📜 **许可证**: MIT
