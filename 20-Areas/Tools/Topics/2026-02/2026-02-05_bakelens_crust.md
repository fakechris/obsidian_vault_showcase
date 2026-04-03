---
title: "BakeLens/crust: AI Agent 安全网关 (425 stars)"
github: "https://github.com/BakeLens/crust"
owner: BakeLens
repo: crust
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, security, ai-agent, gateway, mcp, proxy, golang]
pinboard_tags: [security, agent, gateway]
source_used: github-readme-extract
source_url: "https://github.com/BakeLens/crust"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# BakeLens/crust: AI Agent 安全网关

## 一句话概述

Crust 是一个透明的本地网关，位于 AI Agent 和 LLM 提供商之间，拦截所有工具调用(文件读取、shell 命令、网络请求)，在执行前阻止危险操作，100%本地运行无需代码改动。

## 项目定位

**目标用户**:
- 使用 Claude Code、Codex、Gemini CLI 等 AI 工具的开发者和团队
- 担心 AI Agent 意外读取敏感文件或执行危险命令的安全团队
- 需要 MCP 服务器安全管控的开发者
- 企业级 AI 工具部署的管理员

**解决的问题**:
- **Agent 误读敏感文件**: AI 可能尝试读取 .env、密钥文件等敏感内容
- **危险命令执行**: Agent 可能执行删除、修改等高风险 shell 命令
- **数据泄露风险**: MCP 服务器可能泄露敏感信息到外部
- **缺乏统一管控**: 不同 AI 工具各自为政，无法统一安全管理

**使用场景**:
- 拦截 Agent 读取包含密钥的配置文件
- 阻止危险 shell 命令执行
- 扫描 MCP 服务器响应中的敏感信息泄露
- 统一管控多 Agent 的安全策略

**与同类项目差异**:
- **透明代理**: 无需修改 Agent 代码，通过 HTTP 代理或 MCP 网关接入
- **100% 本地**: 所有数据处理在本地完成，不上传云端
- **多协议支持**: 支持 HTTP Proxy、MCP Stdio/HTTP、ACP 协议
- **DLP 扫描**: 内置数据泄露防护，扫描响应中的敏感信息
- **iOS 支持**: 提供 CrustKit 原生库，支持移动端 Agent

## README 中文简介

**Crust** - 你的 Agent 永远不应该(尝试)读取你的秘密

**核心功能**:
- 拦截所有工具调用(文件读取、shell 命令、网络请求)
- 在执行前阻止危险操作
- 无需代码改动，通过代理或网关方式接入
- 100% 本地运行，数据永不离开你的机器

**五个入口点**:

| 入口点 | 命令 | 功能 |
|--------|------|------|
| HTTP Proxy | `crust start` | 位于 Agent 和 LLM API 之间，扫描请求和响应中的工具调用 |
| MCP Stdio Gateway | `crust wrap` | 包装任何 stdio MCP 服务器，双向拦截 tools/call 和 resources/read |
| MCP HTTP Gateway | `crust wrap` | Streamable HTTP MCP 服务器反向代理 |
| ACP Stdio Proxy | `crust wrap` | 包装 ACP Agent，拦截文件读取和终端命令 |
| Auto-detect | `crust wrap` | 同时检测 MCP 和 ACP 方法 |

**评估流程**:
1. 自我保护检查
2. 输入清理
3. Unicode 规范化
4. 混淆检测
5. DLP 秘密扫描
6. 路径规范化
7. 符号链接解析
8. 规则匹配

**Agent 配置**:

| Agent | 配置 |
|-------|------|
| Claude Code | `ANTHROPIC_BASE_URL=http://localhost:9090` |
| Codex CLI | `OPENAI_BASE_URL=http://localhost:9090/v1` |
| Cursor | Override OpenAI Base URL → `http://localhost:9090/v1` |
| Cline | Base URL → `http://localhost:9090/v1` |
| Windsurf | Provider Base URL → `http://localhost:9090/v1` |
| OpenClaw | `baseUrl: http://localhost:9090` |

**安装**:
```bash
# macOS / Linux / BSD
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/BakeLens/crust/main/install.sh)"

# Windows PowerShell
irm https://raw.githubusercontent.com/BakeLens/crust/main/install.ps1 | iex

# Docker
docker compose up -d
```

**iOS 集成示例**:
```swift
import CrustKit
let engine = CrustEngine()
try engine.initialize()

// 选项1: 本地反向代理
try engine.startProxy(port: 8080, upstreamURL: "https://api.anthropic.com")

// 选项2: URLProtocol (零配置)
CrustURLProtocol.engine = engine
let session = URLSession(configuration: .crustProtected)

// 选项3: 直接评估
let result = await engine.evaluateAsync(toolName: "read_contacts", arguments: [:])
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| HTTP 代理 | 拦截 LLM API 请求响应 | README | 高 |
| MCP 网关 | Stdio 和 HTTP 协议 | README | 高 |
| ACP 代理 | Agent Client Protocol | README | 高 |
| DLP 扫描 | 敏感信息泄露检测 | README | 高 |
| 路径规范化 | 防止路径遍历攻击 | README | 高 |
| 混淆检测 | 检测编码/混淆的恶意请求 | README | 高 |
| iOS 支持 | CrustKit 原生库 | README | 高 |
| 加密日志 | 本地加密存储活动日志 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Crust 架构                                    │
│           (AI Agent 安全网关)                              │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              入口层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐ │  │
│  │   │ HTTP Proxy   │ MCP Gateway  │ ACP Proxy    │ │  │
│  │   │              │ (Stdio/HTTP) │              │ │  │
│  │   │ crust start  │ crust wrap   │ crust wrap   │ │  │
│  │   └──────────────┴──────────────┴──────────────┘ │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              评估管道层                            │  │
│  │                                                  │  │
│  │   1. 自我保护检查                                │  │
│  │   2. 输入清理                                    │  │
│  │   3. Unicode 规范化                              │  │
│  │   4. 混淆检测                                    │  │
│  │   5. DLP 秘密扫描                                │  │
│  │   6. 路径规范化                                  │  │
│  │   7. 符号链接解析                                │  │
│  │   8. 规则匹配                                    │  │
│  │                                                  │  │
│  │   (每步微秒级执行)                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              规则引擎层                            │  │
│  │                                                  │  │
│  │   • 文件访问规则                                 │  │
│  │   • 命令执行规则                                 │  │
│  │   • 网络请求规则                                 │  │
│  │   • 自定义规则                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              日志存储层                            │  │
│  │                                                  │  │
│  │   • 本地加密存储                                 │  │
│  │   • 审计追踪                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              CrustKit (iOS)                      │  │
│  │                                                  │  │
│  │   • 本地反向代理                                 │  │
│  │   • URLProtocol 拦截                             │  │
│  │   • 内容扫描                                     │  │
│  │   • 移动端 PII 保护                              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| HTTP Proxy | cmd/ | HTTP 代理入口 | 入口 |
| MCP Gateway | pkg/libcrust/ | MCP 协议网关 | 核心 |
| 规则引擎 | internal/ | 规则匹配和执行 | 核心 |
| DLP 扫描 | internal/ | 敏感信息检测 | 安全 |
| iOS 库 | ios/CrustKit/ | 移动端 SDK | 扩展 |

## 运行与开发方式

**快速启动**:
```bash
# 安装
curl -fsSL https://raw.githubusercontent.com/BakeLens/crust/main/install.sh | bash

# 启动代理
crust start

# 查看状态
crust status
crust status --agents  # 检测运行中的 AI Agent

# 查看日志
crust logs -f

# 诊断
crust doctor

# 停止
crust stop
```

**MCP 网关使用**:
```bash
crust wrap -- npx -y @modelcontextprotocol/server-filesystem /path/to/dir
```

**Docker**:
```bash
docker build -t crust https://github.com/BakeLens/crust.git
docker run -p 9090:9090 crust
```

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `crust start` | 启动 HTTP 代理 |
| `crust stop` | 停止 crust |
| `crust status` | 检查状态 |
| `crust logs` | 查看日志 |
| `crust doctor` | 诊断端点 |
| `crust wrap` | MCP/ACP 网关包装 |

**环境变量**:
- `CRUST_PORT`: 代理端口(默认 9090)
- `CRUST_LOG_LEVEL`: 日志级别
- `CRUST_CONFIG`: 配置文件路径

**移动端保护**:
| 类别 | 阻止的工具 | 规则 |
|------|------------|------|
| PII | contacts, photos, calendar, location... | protect-mobile-pii |
| Keychain | keychain 读/写/删除 | protect-os-keychains |
| Clipboard | clipboard read | protect-mobile-clipboard |

## 数据流 / 控制流

```
Agent 发送请求
    ↓
Crust 入口(Proxy/Gateway)
    ↓
评估管道(8 步检查)
    ↓
规则匹配
    ↓
┌─────────────┐
│ 允许?       │
└─────────────┘
    ↓           ↓
  是           否
    ↓           ↓
转发请求     阻止并记录
    ↓
返回响应
    ↓
DLP 扫描响应
    ↓
返回给 Agent
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Go | 主要语言 | 高 |
| Swift | iOS 库 | 高 |
| SQLite | 加密日志存储 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README 清晰 | 高 |
| 上手难度 | 低 | 一键安装 | 低 |
| 架构复杂度 | 中 | 多协议支持 | 中 |
| 外部依赖 | 低 | 100% 本地 | 低 |
| Stars | 中 | 425 stars | 中 |
| 安全审计 | 中 | 需要安全审查 | 中 |

**注意事项**:
- 需要仔细配置规则，避免过度拦截影响 Agent 功能
- 生产环境使用前建议进行安全审计
- iOS 集成需要 Xcode 和 Swift 环境

## 关联概念

- [[Claude-Code]] - Anthropic CLI 编码工具
- [[MCP]] - Model Context Protocol
- [[ACP]] - Agent Client Protocol
- [[DLP]] - Data Loss Prevention
- [[Security-Gateway]] - 安全网关模式

---

> 来源: [GitHub](https://github.com/BakeLens/crust) | 置信度: 基于 GitHub README
> 👤 **作者**: BakeLens
> ⭐ **Stars**: 425
> 🔗 **网站**: crust.io
> 📜 **许可证**: MIT
