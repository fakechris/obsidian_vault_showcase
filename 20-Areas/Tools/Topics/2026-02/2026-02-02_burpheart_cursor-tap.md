---
title: "burpheart/cursor-tap: Cursor IDE gRPC 流量分析工具 (279 stars)"
github: "https://github.com/burpheart/cursor-tap"
owner: burpheart
repo: cursor-tap
date: 2026-02-02
batch_date: 2026-02-02
type: github-project
tags: [github, cursor, reverse-engineering, grpc, mitm, security]
pinboard_tags: [cursor, reverse]
source_used: github-readme-extract
source_url: "https://github.com/burpheart/cursor-tap"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# burpheart/cursor-tap: Cursor IDE gRPC 流量分析工具

## 一句话概述

Cursor-Tap 是一个 Cursor IDE gRPC 中间人流量分析工具，可以解密 TLS、反序列化 protobuf、实时展示 AI 对话产生的 RPC 请求和响应。

## 项目定位

**目标用户**:
- 需要逆向分析 Cursor IDE 通信的安全研究者
- 想了解 Cursor 内部工作原理的开发者
- 需要拦截 gRPC 流量进行调试的技术人员

**解决的问题**:
- **gRPC 流量不可读**: Cursor 和后端使用 gRPC + Connect Protocol，Body 是二进制 protobuf
- **缺乏 proto 定义**: 官方未公开 proto 定义，用 Burp/Fiddler 抓到的都是二进制
- **实时分析困难**: 无法实时查看 AI 对话的具体内容和 RPC 调用

**使用场景**:
- 逆向分析 Cursor IDE 的 AI 对话流程
- 研究 Cursor 的代码补全和用户行为上报机制
- 学习 gRPC 中间人攻击和 protobuf 反序列化技术

**与同类项目差异**:
- **专为 Cursor 设计**: 从 Cursor 客户端 JS 代码中提取 proto 定义
- **实时 WebUI**: WebSocket 实时推送，四栏布局展示服务树/调用列表/帧列表/详情
- **完整 proto 定义**: 已提取并整理 Cursor 的 proto 文件

## README 中文简介

**Cursor-Tap** - Cursor IDE gRPC 通信流量分析工具

**为什么做这个**: Cursor 和后端通信全是 gRPC，二进制 protobuf 难以分析，想看 AI 对话具体内容很麻烦。

**核心原理**:
1. **MITM 代理**: 在 Cursor 和 api2.cursor.sh 之间插层，用自签 CA 解密 TLS
2. **Proto 提取**: 从 Cursor 客户端 JS 代码里提取 proto 定义
3. **实时解析**: 解析 Connect Protocol 的 envelope framing，反序列化每帧 protobuf
4. **WebUI 展示**: WebSocket 实时推送到前端，四栏布局展示

**快速开始**:
```bash
# 1. 启动代理
go run ./cmd/proxy
# 默认监听 localhost:8080 (HTTP 代理) 和 localhost:9090 (WebUI + WebSocket)

# 2. 配置 Cursor 代理环境变量
# macOS/Linux:
export HTTP_PROXY=http://localhost:8080
export HTTPS_PROXY=http://localhost:8080
export NODE_EXTRA_CA_CERTS=/path/to/ca.crt

# 3. 启动 WebUI
cd web && npm install && npm run dev
# 打开 http://localhost:3000 查看流量
```

**能看到的 RPC 方法**:
- `AiService/RunSSE`: AI 对话主通道，包括 AI 思考、文本生成、工具调用
- `BidiService/BidiAppend`: 用户消息和工具执行结果
- `AiService/StreamCpp`: 代码补全请求和建议
- `CppService/RecordCppFate`: 补全结果的接受/拒绝反馈
- `AiService/Batch`: 用户行为上报

**相关文章**: [Cursor 逆向笔记 1](cursor-reverse-notes-1.md) — 如何拦截解析 Cursor 的 gRPC 通信流量

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| TLS 解密 | 自签 CA 中间人攻击解密 TLS | README | 高 |
| Protobuf 反序列化 | 提取并解析 Cursor proto 定义 | README | 高 |
| 实时流量展示 | WebSocket + WebUI 实时推送 | README | 高 |
| Connect Protocol 解析 | 解析 gRPC Connect Protocol framing | README | 高 |
| 多 RPC 方法支持 | 覆盖 AI 对话、代码补全、用户行为上报 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Cursor-Tap 系统架构                          │
│           (Cursor IDE gRPC 流量分析工具)                    │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              代理层                              │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │   MITM 代理   │    │ 自签 CA 证书 │        │  │
│  │   │ localhost:8080│    │ 动态签发     │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  │   命令: go run ./cmd/proxy                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              解析层                              │  │
│  │                                                  │  │
│  │   ┌────────────────────────────────────────┐   │  │
│  │   │           internal/httpstream          │   │  │
│  │   │                                          │   │  │
│  │   │  • grpc.go — protobuf 反序列化          │   │  │
│  │   │  • parser.go — Connect Protocol 解析    │   │  │
│  │   │  • recorder.go — 流量记录             │   │  │
│  │   └────────────────────────────────────────┘   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Proto 定义层                        │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │ cursor_proto/ │    │ 从 Cursor JS │        │  │
│  │   │              │    │ 提取的 proto │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              WebUI 展示层                         │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │  Next.js 前端 │    │ WebSocket    │        │  │
│  │   │  localhost:9090    │ 实时推送     │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  │   四栏布局: 服务树 | 调用列表 | 帧列表 | 详情   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 代理入口 | `cmd/proxy/` | HTTP CONNECT 代理 | 流量入口 |
| CA 管理 | `internal/ca/` | 自签证书动态签发 | 安全基础 |
| 代理核心 | `internal/proxy/` | HTTP CONNECT 代理实现 | 流量转发 |
| gRPC 解析 | `internal/httpstream/` | protobuf 反序列化 | 解析核心 |
| Proto 定义 | `cursor_proto/` | 提取的 proto 文件 | 数据结构 |
| WebUI | `web/` | Next.js 前端 | 展示层 |

## 运行与开发方式

**前置要求**:
- Go 环境
- Node.js (WebUI)
- Cursor IDE (被分析目标)

**快速开始**:
```bash
# 1. 克隆仓库
git clone https://github.com/burpheart/cursor-tap && cd cursor-tap

# 2. 启动代理
go run ./cmd/proxy
# 监听 localhost:8080 (代理) 和 localhost:9090 (WebUI)

# 3. 配置 Cursor 环境变量
export HTTP_PROXY=http://localhost:8080
export HTTPS_PROXY=http://localhost:8080
export NODE_EXTRA_CA_CERTS=/path/to/ca.crt
# CA 证书自动生成在 ~/.cursor-tap/ca.crt

# 4. 启动 WebUI
cd web && npm install && npm run dev
```

**使用**:
- 打开 http://localhost:3000 查看实时流量
- 四栏布局: 服务树 / 调用列表 / 帧列表 / 详情

**逆向笔记**:
- 查看 `cursor-reverse-notes-1.md` 了解拦截解析 Cursor gRPC 的技术细节

## 外部接口

**代理接口**:
| 地址 | 功能 |
|------|------|
| localhost:8080 | HTTP 代理入口 |
| localhost:9090 | WebUI + WebSocket |
| http://localhost:3000 | WebUI 前端 |

**环境变量**:
```bash
HTTP_PROXY=http://localhost:8080
HTTPS_PROXY=http://localhost:8080
NODE_EXTRA_CA_CERTS=/path/to/ca.crt
```

**观察的 RPC 服务**:
| 服务 | 方法 | 说明 |
|------|------|------|
| AiService | RunSSE | AI 对话主通道 |
| BidiService | BidiAppend | 用户消息和工具结果 |
| AiService | StreamCpp | 代码补全 |
| CppService | RecordCppFate | 补全反馈 |
| AiService | Batch | 用户行为上报 |

## 数据流 / 控制流

```
Cursor IDE ←──TLS──→ api2.cursor.sh
     │
     │ (被拦截)
     ▼
┌────────────────────────────────────────────────────────────┐
│ 1. MITM 代理层                                              │
│    - HTTP CONNECT 代理 localhost:8080                       │
│    - 自签 CA 解密 TLS                                       │
│    - 证书自动生成 ~/.cursor-tap/ca.crt                     │
└────────────────────────────────────────────────────────────┘
     │
     ▼
┌────────────────────────────────────────────────────────────┐
│ 2. gRPC 解析层                                              │
│    - Connect Protocol envelope framing 解析                 │
│    - Protobuf 反序列化 (使用 cursor_proto/)                │
│    - 流量记录到 recorder                                   │
└────────────────────────────────────────────────────────────┘
     │
     ▼
┌────────────────────────────────────────────────────────────┐
│ 3. WebSocket 推送层                                         │
│    - 实时推送到 WebUI                                       │
│    - 四栏布局展示                                           │
└────────────────────────────────────────────────────────────┘
     │
     ▼
WebUI (localhost:3000) 展示服务树/调用列表/帧列表/详情
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Go | 代理后端 | 高 |
| TypeScript/Next.js | WebUI 前端 | 高 |
| gRPC Connect Protocol | 协议解析 | 高 |
| Protobuf | 反序列化 | 高 |
| WebSocket | 实时通信 | 高 |
| MITM/TLS | 证书劫持 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 清晰，逆向笔记详细 |
| 上手难度 | 中 | 需要配置代理和证书 | 中 |
| 架构复杂度 | 中 | 涉及 MITM、TLS、protobuf | 中 |
| 外部依赖 | 低 | 依赖 Cursor IDE 作为目标 | 低 |
| Stars | 低 | 279 stars |
| 法律风险 | 高 | 逆向工程可能违反 Cursor 服务条款 |

**注意事项**:
- 本项目涉及逆向工程，可能违反 Cursor 服务条款
- 仅供学习研究，不建议在生产环境使用
- 需要配置系统信任自签 CA 证书
- Cursor 更新可能导致 proto 定义失效

## 关联概念

- [[Reverse-Engineering]] - 逆向工程
- [[gRPC]] - gRPC 协议
- [[Connect-Protocol]] - Connect Protocol
- [[Protobuf]] - Protocol Buffers
- [[MITM]] - 中间人攻击
- [[TLS]] - TLS/SSL
- [[Cursor-IDE]] - Cursor 编辑器

---

> 来源: [GitHub](https://github.com/burpheart/cursor-tap) | 置信度: 基于 GitHub README
> 👤 **作者**: burpheart
> ⭐ **Stars**: 279
> 📝 **文章**: [Cursor 逆向笔记 1](cursor-reverse-notes-1.md)
