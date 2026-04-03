---
title: "TraderAlice/OpenAlice: AI交易Agent引擎 (3.1k stars)"
github: "https://github.com/TraderAlice/OpenAlice"
owner: TraderAlice
repo: OpenAlice
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, typescript, ai, trading, crypto, finance, agent]
pinboard_tags: [ai, trading, crypto]
source_used: github-readme-extract
source_url: "https://github.com/TraderAlice/OpenAlice"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# TraderAlice/OpenAlice: AI交易Agent引擎

## 一句话概述

OpenAlice是一个文件驱动的AI交易Agent引擎，将"vibe coding"范式带入量化交易领域，支持多券商、多AI提供商、Trading-as-Git工作流，24/7运行在本地笔记本上。

## 项目定位

**目标用户**:
- 个人量化交易者
- 算法交易开发者
- 寻求AI辅助交易决策的投资者
- 需要多账户管理的交易者

**解决的问题**:
- **交易执行复杂**: 券商API各异，难以统一管理
- **决策不可追溯**: 传统交易缺乏完整决策记录
- **风险控制不足**: 缺乏预执行安全检查
- **AI上下文丢失**: 不同会话间无法保持交易上下文
- **多工具切换困难**: Claude、OpenAI等AI工具切换麻烦

**使用场景**:
- 多券商账户统一管理
- AI辅助交易决策
- 量化策略回测和执行
- 7×24小时自动监控
- 股票、期权、期货、加密货币交易

**与同类项目差异**:
- **文件驱动**: Markdown定义人设，JSON定义配置，无数据库无容器
- **Trading-as-Git**: stage → commit → push → 审批执行
- **统一交易账户(UTA)**: 每个账户自带券商连接、Git历史、风控管道
- **多AI提供商**: 运行时切换Claude Agent SDK和Vercel AI SDK
- **OS原生**: 可控制浏览器、Telegram、本地设备

## README 中文简介

**Open Alice** - 你的个人华尔街

一个人的交易 desk：研究部门、量化团队、交易大厅、风控管理——全部运行在本地笔记本上，24/7不间断。

**核心特性**:
- **文件驱动**: Markdown定义persona和任务，JSON定义配置，JSONL存储对话
- **推理驱动**: 每个交易决策基于持续推理和信号混合
- **OS原生**: 可搜索网页、发送Telegram消息、连接本地设备
- **多AI提供商**: Claude (Agent SDK) 和 Vercel AI SDK 运行时切换
- **统一交易账户(UTA)**: 每个账户整合券商连接、Git历史、风控管道
- **Trading-as-Git**: stage订单 → commit带消息 → push执行

**支持券商**:
- CCXT (100+加密货币交易所)
- Alpaca (美股)
- Interactive Brokers (股票、期权、期货、债券)

**市场数据**:
- TypeScript原生OpenBB引擎 (opentypebb)
- 股票基本面、技术指标、宏观经济数据
- 统一symbol搜索 (marketSearchForResearch)

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Trading-as-Git | Git式交易工作流 (stage→commit→push) | README | 高 |
| 统一交易账户 | UTA整合券商+历史+风控 | README | 高 |
| 多券商支持 | CCXT/Alpaca/IBKR | README | 高 |
| 风控管道 | 预执行安全检查 | README | 高 |
| 多AI切换 | Claude/Vercel AI SDK | README | 高 |
| 市场数据 | OpenBB原生引擎 | README | 高 |
| 新闻RSS | 背景RSS收集+搜索 | README | 高 |
| 认知状态 | 持久化记忆和情绪跟踪 | README | 高 |
| Cron调度 | AI驱动的定时任务 | README | 高 |
| 进化模式 | AI可修改自身源代码 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              OpenAlice 架构                                │
│           (AI交易Agent引擎)                                │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              提供商层                              │  │
│  │                                                  │  │
│  │   ┌──────────────────┬──────────────────┐      │  │
│  │   │ Claude           │ Vercel AI SDK    │      │  │
│  │   │ (Agent SDK)      │ (多模型)         │      │  │
│  │   └──────────────────┴──────────────────┘      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心层                                │  │
│  │                                                  │  │
│  │   • AgentCenter (AI编排)                      │  │
│  │   • ProviderRouter (提供商路由)               │  │
│  │   • ToolCenter (工具注册)                     │  │
│  │   • EventLog (事件日志)                       │  │
│  │   • ConnectorCenter (连接器中心)              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              领域层 (Domain)                       │  │
│  │                                                  │  │
│  │   ┌────────────┬────────────┬────────────┐    │  │
│  │   │ 市场数据   │ 交易(UTA)  │ 新闻收集   │    │  │
│  │   ├────────────┼────────────┼────────────┤    │  │
│  │   │ 分析       │ 大脑       │ 浏览器     │    │  │
│  │   └────────────┴────────────┴────────────┘    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              接口层                                │  │
│  │                                                  │  │
│  │   ┌────────────┬────────────┬────────────┐    │  │
│  │   │ Web UI     │ Telegram   │ MCP        │    │  │
│  │   │ (本地聊天) │ (移动)     │ (工具暴露) │    │  │
│  │   └────────────┴────────────┴────────────┘    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心编排 | `src/core/` | AgentCenter、ProviderRouter、ToolCenter | 核心 |
| 交易领域 | `src/domain/trading/` | UTA、券商、Git、风控 | 核心 |
| 市场数据 | `src/domain/market-data/` | OpenBB引擎、多资产数据 | 核心 |
| 工具定义 | `src/tool/` | AI工具桥接层 | 核心 |
| 连接器 | `src/connectors/` | Web/Telegram/MCP | 接口 |
| 任务调度 | `src/task/` | Cron、Heartbeat | 后台 |
| 数据存储 | `data/` | 配置、会话、交易历史 | 持久化 |

## 运行与开发方式

**环境要求**:
- Node.js 22+
- pnpm 10+
- Claude Code CLI (已认证)

**快速开始**:
```bash
git clone https://github.com/TraderAlice/OpenAlice.git
cd OpenAlice
pnpm install && pnpm build
pnpm dev
```

**开发模式**:
```bash
pnpm dev        # 启动后端(3002) + watch模式
pnpm dev:ui     # 启动前端开发服务器(5173)
pnpm build      # 生产构建
pnpm test       # 运行测试
```

**默认配置**:
- 使用本地Claude Code登录 (Claude Pro/Max订阅)
- 无需API key
- 端口3002 (UI在构建后可用)
- 前端开发用5173 (带热重载)

## 外部接口

**AI提供商配置** (`ai-provider.json`):
| 提供商 | 说明 |
|--------|------|
| agent-sdk | Claude Agent SDK (默认，支持OAuth/API key) |
| vercel-ai-sdk | 支持Anthropic/OpenAI/Google等 |

**统一交易账户(UTA)**:
- 每个账户独立券商连接
- Git-like操作历史 (commit带8字符hash)
- 风控管道 (最大仓位、冷却时间、symbol白名单)
- 定期快照和权益曲线

**Trading-as-Git命令**:
| 命令 | 功能 |
|------|------|
| stagePlaceOrder | 暂存下单 |
| stageClosePosition | 暂存平仓 |
| commit | 提交带消息 |
| push | 执行（需审批） |
| tradingLog | 查看历史 |
| tradingShow | 显示详情 |

**风控(Guard)**:
- 最大持仓限制
- 交易冷却时间
- Symbol白名单

**市场数据**:
- 公司概况、财务报表、分析师预期
- 内幕交易、市场热点
- 技术指标计算
- 宏观经济数据

**新闻系统**:
- 背景RSS收集
- 归档搜索 (globNews/grepNews/readNews)

**文件组织**:
```
data/
├── config/          # JSON配置
├── sessions/        # JSONL对话历史
├── brain/           # 记忆和情绪日志
├── trading/         # 交易历史+快照
├── news-collector/  # 新闻归档
├── cron/            # 定时任务定义
└── event-log/       # 事件日志
```

## 数据流 / 控制流

```
用户输入 (Web/Telegram/MCP)
    ↓
AgentCenter编排
    ↓
工具选择和执行
    ↓
领域逻辑处理 (UTA/市场数据/新闻)
    ↓
风控检查 (Guard)
    ↓
券商执行 (CCXT/Alpaca/IBKR)
    ↓
快照记录和权益曲线更新
    ↓
事件日志和会话存储
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (78.5%) | 高 |
| Node.js 22+ | 运行时 | 高 |
| pnpm | 包管理 | 高 |
| Claude Agent SDK | 默认AI后端 | 高 |
| Vercel AI SDK | 备选AI后端 | 高 |
| CCXT | 加密货币交易 | 高 |
| Interactive Brokers | 传统市场交易 | 高 |
| OpenBB | 市场数据 | 高 |
| Hono | Web框架 | 中 |
| Telegram grammY | Bot框架 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细架构文档 | 高 |
| 上手难度 | 中 | 需要Node.js和Claude Code | 中 |
| 架构复杂度 | 高 | 多领域+多券商+多AI | 高 |
| 外部依赖 | 高 | 需要券商账户和AI API | 高 |
| Stars | 高 | 3.1k stars | 高 |
| 维护状态 | 高 | 活跃开发 | 高 |

**⚠️ 重要警告**:
> Open Alice是实验性软件，处于积极开发中。许多功能和接口不完整，可能会有破坏性变更。除非您完全理解并接受所涉及的风险，否则请勿将本软件用于真实资金的实时交易。作者不提供正确性、可靠性或盈利能力的保证，也不对财务损失承担任何责任。

**关键概念**:
- **UTA (Unified Trading Account)**: 统一交易账户，整合券商+历史+风控
- **Trading-as-Git**: Git式交易工作流
- **Evolution Mode**: 进化模式，允许AI修改自身源代码
- **Heartbeat**: 定期检查，决定是否向用户发送消息

## 关联概念

- [[Claude-Agent-SDK]] - Anthropic Agent SDK
- [[Vercel-AI-SDK]] - Vercel AI SDK
- [[CCXT]] - 加密货币交易库
- [[Interactive-Brokers]] - 券商API
- [[Alpaca]] - 美股交易API
- [[OpenBB]] - 开源金融数据平台
- [[Quantitative-Trading]] - 量化交易
- [[Algorithmic-Trading]] - 算法交易
- [[Git-Workflow]] - Git工作流模式
- [[MCP]] - Model Context Protocol

---

> 来源: [GitHub](https://github.com/TraderAlice/OpenAlice) | 置信度: 基于 GitHub README
> 👤 **作者**: TraderAlice
> ⭐ **Stars**: 3.1k
> 🔗 **官网**: [openalice.ai](https://openalice.ai)
> 📜 **许可证**: AGPL-3.0
