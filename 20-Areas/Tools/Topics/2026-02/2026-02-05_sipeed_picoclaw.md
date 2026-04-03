---
title: "sipeed/picoclaw: 超轻量级个人 AI 助手 (27.1k stars)"
github: "https://github.com/sipeed/picoclaw"
owner: sipeed
repo: picoclaw
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, go, ai, assistant, embedded, lightweight]
pinboard_tags: [go, ai, assistant, embedded]
source_used: github-readme-extract
source_url: "https://github.com/sipeed/picoclaw"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# sipeed/picoclaw: 超轻量级个人 AI 助手

## 一句话概述

PicoClaw 是一个由 Sipeed 发起的独立开源项目，完全用 Go 从头编写（非 OpenClaw/NanoBot 分支），受 NanoBot 启发，在 $10 硬件上运行仅需 <10MB RAM — 比 OpenClaw 少 99% 内存，比 Mac mini 便宜 98%！

## 项目定位

**目标用户**:
- 寻求极轻量级 AI 助手的用户
- 嵌入式设备开发者
- 需要低成本 AI 方案的团队
- Go 语言爱好者

**解决的问题**:
- **资源消耗高**: 现有 AI 助手需要大量内存和计算资源
- **成本高**: 运行 AI 助手需要昂贵硬件
- **依赖复杂**: 多数项目基于现有框架修改，依赖繁重
- **架构不透明**: 自举过程不明确，难以理解和定制

**使用场景**:
- 嵌入式设备 AI 助手
- 低资源环境 AI 应用
- 个人 AI 助手（轻量版）
- 边缘计算场景

**与同类项目差异**:
- **超轻量**: <10MB RAM，$10 硬件
- **Go 原生**: 完全用 Go 从头编写，非分支项目
- **自举架构**: AI Agent 本身驱动架构迁移和代码优化
- **独立项目**: 不 fork OpenClaw、NanoBot 或其他项目
- **99% 内存节省**: 相比 OpenClaw

## README 中文简介

**PicoClaw** - 超高效的 Go 语言 AI 助手

**$10 硬件 · 10MB RAM · 毫秒启动 · Let's Go, PicoClaw!**

**语言**: 中文 | 日本語 | Português | Tiếng Việt | Français | Italiano | Bahasa Indonesia | Malay | English

**⚠️ 安全声明**:

**无加密货币**: PicoClaw 未发行任何官方代币或加密货币。pump.fun 或其他交易平台上的所有声称都是诈骗。

**官方域名**: 唯一官方网站是 picoclaw.io，公司网站是 sipeed.com

**警惕**: 许多 .ai/.org/.com/.net/... 域名已被第三方注册。不要相信它们。

**注意**: PicoClaw 处于早期快速开发阶段。可能存在未解决的安全问题。在 v1.0 之前不要部署到生产环境。

**注意**: PicoClaw 最近合并了许多 PR。近期构建可能使用 10-20MB RAM。功能稳定后计划进行资源优化。

**📢 新闻**:

**2026-03-31** 📱 Android 支持！PicoClaw 现在可在 Android 上运行！在 picoclaw.io 下载 APK

**2026-03-25** 🚀 v0.2.4 发布！Agent 架构大修（SubTurn、Hooks、Steering、EventBus）、微信/企业微信集成、安全加固（.security.yml、敏感数据过滤）、新提供商（AWS Bedrock、Azure、小米 MiMo）和 35 个 bug 修复。PicoClaw 已达 26K Stars！

**2026-03-17** 🚀 v0.2.3 发布！系统托盘 UI（Windows & Linux）、子代理状态查询（spawn_status）、实验性 Gateway 热重载、Cron 安全门控和 2 个安全修复。PicoClaw 已达 25K Stars！

**项目说明**:

PicoClaw 是由 Sipeed 发起的独立开源项目，完全用 Go 从头编写 —— 不是 OpenClaw、NanoBot 或任何其他项目的分支。

PicoClaw 是一个受 NanoBot 启发的超轻量级个人 AI 助手。它通过"自举"过程从头用 Go 重建 —— AI Agent 本身驱动架构迁移和代码优化。

在 $10 硬件上运行，仅需 <10MB RAM — 比 OpenClaw 少 99% 内存，比 Mac mini 便宜 98%！

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 超轻量 | <10MB RAM | README | 高 |
| 低成本 | $10 硬件 | README | 高 |
| Go 原生 | 完全 Go 编写 | README | 高 |
| 自举架构 | AI 驱动开发 | README | 高 |
| 独立项目 | 非分支 | README | 高 |
| Android 支持 | Android APK | README | 高 |
| 微信集成 | 微信/企业微信 | README | 高 |
| 多提供商 | AWS/Azure/小米 MiMo | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              PicoClaw 架构                                   │
│           (超轻量级 AI 助手)                                 │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              接口层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ CLI          │ Android      │ Web          ││  │
│  │   │ (命令行)     │ (APK)        │ (Web UI)     ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ 微信         │ 企业微信     │ Gateway      ││  │
│  │   │ (WeChat)     │ (WeCom)      │ (API)        ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心层 (Go)                           │  │
│  │                                                  │  │
│  │   • Agent 运行时                                 │  │
│  │   • SubTurn 架构                                 │  │
│  │   • Hooks 系统                                   │  │
│  │   • Steering 控制                                │  │
│  │   • EventBus                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              提供商层                              │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ AWS Bedrock  │ Azure        │ 小米 MiMo    ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ OpenAI       │ Anthropic    │ 更多...       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 命令 | `cmd/` | CLI 入口 | 核心 |
| 配置 | `config/` | 配置管理 | 核心 |
| 包 | `pkg/` | 核心库 | 核心 |
| 示例 | `examples/` | 示例代码 | 示例 |
| Web | `web/` | Web 界面 | 接口 |
| Docker | `docker/` | 容器化 | 部署 |

## 运行与开发方式

**快速开始**:
```bash
# 下载预编译二进制
# 或从源码构建
git clone https://github.com/sipeed/picoclaw.git
cd picoclaw
go build -o picoclaw ./cmd

# 运行
./picoclaw
```

**Docker**:
```bash
docker run sipeed/picoclaw
```

**Android**:
下载 APK: picoclaw.io

**开发**:
```bash
# 克隆
git clone https://github.com/sipeed/picoclaw.git
cd picoclaw

# 构建
go build ./cmd

# 测试
go test ./...
```

## 外部接口

**CLI**:
```bash
picoclaw [command] [flags]
```

**Gateway API**:
- 实验性热重载支持
- RESTful API

**微信集成**:
- 微信公众号
- 企业微信

## 数据流 / 控制流

```
用户输入 (CLI/微信/Android/Web)
    ↓
Agent Core (Go)
    ↓
SubTurn 处理
    ↓
LLM Provider (AWS/Azure/MiMo/OpenAI)
    ↓
Hooks / EventBus
    ↓
响应返回
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Go | 核心语言 | 高 |
| Docker | 容器化 | 高 |
| SQLite | 可能用于存储 | 中 |
| WebSocket | 实时通信 | 中 |
| REST API | Gateway | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 信息丰富，多语言 | 中 |
| 上手难度 | 低 | 预编译二进制，Docker | 低 |
| 架构复杂度 | 中 | Agent 架构大修中 | 中 |
| 外部依赖 | 低 | Go 原生，依赖少 | 低 |
| Stars | 高 | 27.1k stars | 高 |
| 维护状态 | 高 | 快速迭代，活跃更新 | 高 |

**⚠️ 重要警告**:
- **v1.0 前不要用于生产**: 存在未解决安全问题
- **近期构建内存使用**: 可能使用 10-20MB（计划优化）
- **诈骗警告**: 无官方代币，警惕 pump.fun 等平台的诈骗
- **域名警告**: 仅信任 picoclaw.io 和 sipeed.com

**版本历史**:
- v0.2.4 (2026-03-25): Agent 架构大修，35 bug 修复
- v0.2.3 (2026-03-17): 系统托盘 UI，安全修复
- Android 支持 (2026-03-31)

## 关联概念

- [[NanoBot]] - 灵感来源
- [[OpenClaw]] - 对比基准
- [[Go]] - Go 编程语言
- [[Embedded-AI]] - 嵌入式 AI
- [[Edge-Computing]] - 边缘计算
- [[WeChat-Bot]] - 微信机器人
- [[AWS-Bedrock]] - AWS LLM 服务
- [[Azure-OpenAI]] - Azure LLM 服务

---

> 来源: [GitHub](https://github.com/sipeed/picoclaw) | 置信度: 基于 GitHub README
> 👤 **作者**: Sipeed
> ⭐ **Stars**: 27.1k
> 🔗 **官网**: [picoclaw.io](https://picoclaw.io)
> 🔗 **公司**: [sipeed.com](https://sipeed.com)
> 📜 **许可证**: MIT
