---
title: "tinyfish-io/tinyfish-cookbook: TinyFish Web Agent 示例集 (1.4k stars)"
github: "https://github.com/tinyfish-io/tinyfish-cookbook"
owner: tinyfish-io
repo: tinyfish-cookbook
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, web-agent, api, automation, cookbook]
pinboard_tags: [web-agent, api, automation]
source_used: github-readme-extract
source_url: "https://github.com/tinyfish-io/tinyfish-cookbook"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# tinyfish-io/tinyfish-cookbook: TinyFish Web Agent 示例集

## 一句话概述

TinyFish Cookbook 是一个 Web Agent 示例集合，展示如何使用 TinyFish API 将真实网站转化为可编程数据源，包含 20+ 实际应用场景如价格比较、库存搜索、研究助手等。

## 项目定位

**目标用户**:
- 需要 Web 自动化和数据提取的开发者
- 希望了解 Web Agent 应用场景的工程师
- 寻求无 API 网站数据访问方案的团队
- 需要实时网络数据的项目

**解决的问题**:
- **无 API 网站**: 许多网站没有提供 API，难以程序化访问
- **浏览器自动化复杂**: headless browser、选择器、代理管理繁琐
- **动态内容**: 表单、过滤器、日历等动态内容难以处理
- **反爬虫**: 网站反爬虫机制限制数据获取
- **多站点协调**: 需要同时处理多个网站的场景复杂

**使用场景**:
- 电商价格比较和库存监控
- 学术研究和文献检索
- 竞品分析和市场调研
- 物流和供应链跟踪
- 餐厅、酒店、奖学金等信息聚合

**与同类项目差异**:
- **SOTA 性能**: Mind2Web 基准测试 90%，超越 Gemini 21 分
- **自然语言目标**: 无需复杂选择器，用自然语言描述目标
- **真实浏览器**: 真实浏览器自动化，支持多步骤流程
- **内置隐身模式**: 包含代理轮换和隐身配置
- **生产级日志**: 完整的可观测性和调试能力

## README 中文简介

**TinyFish Cookbook** - TinyFish Web Agent 示例集合

**TinyFish 是什么?**

SOTA Web Agent API，让您将真实网站视为可编程界面。无需处理 headless browser、选择器、代理和各种边界情况，只需调用单个 API，传入目标和 URL，即可获得干净的 JSON 数据。它处理导航、表单、过滤器、动态内容、代理和多站点多步骤流程。

**企业级基础设施**:
被 Google、Doordash 和 Classpass 等大型企业使用的基础设施，现在对所有人开放！

**为什么选 TinyFish?**

| 特性 | 说明 |
|------|------|
| 🕸️ 全托管浏览器和 Agent | 一个 API 包含所有基础设施 |
| 🌐 任意网站 → API | 将无 API 的网站转化为可编程数据源 |
| 💬 自然语言目标 | URL + 纯英语描述，返回结构化 JSON |
| 🤖 真实浏览器自动化 | 多步骤流程、表单、过滤器、日历、动态内容 |
| 🥷 内置隐身模式 | 包含轮换代理 + 隐身配置（无额外费用）|
| 📊 生产级日志 | 每次运行的完整可观测性和调试 |
| 🔌 灵活集成 | HTTP API、可视化 Playground 或 MCP 服务器 |

**SOTA 性能**:
Mind2Web 基准测试 90%，超越 Gemini 21 分、OpenAI 29 分、Anthropic 34 分。并行运行全部 300 个任务并公开发布每次运行。

**食谱集合**:

每个文件夹都是独立项目，展示如何解决真实世界问题：

| 食谱 | 描述 |
|------|------|
| anime-watch-hub | 帮助找到免费阅读/观看漫画/动漫的网站 |
| bestbet | 体育博彩赔率比较工具 |
| code-reference-finder | AI 驱动的代码片段分析器，从 GitHub 和 Stack Overflow 查找真实使用示例 |
| competitor-analysis | 实时竞品定价智能仪表板 |
| competitor-scout-cli | 跨多个网站研究竞品功能决策的自然语言 CLI 工具 |
| concept-discovery-system | 跨 GitHub、Dev.to 和 Stack Overflow 发现类似现有项目的创意验证器 |
| fast-qa | 带并行测试执行和实时浏览器预览的无代码 QA 测试平台 |
| game-buying-guide | 跨 10 个游戏平台并行比较定价和优惠的购买决策工具 |
| lego-hunter | 跨 15+ 零售商查找稀有乐高套装的全球库存搜索工具 |
| loan-decision-copilot | 跨银行和地区的 AI 驱动贷款比较工具 |
| logistics-sentry | 港口拥堵和承运商风险跟踪的物流智能平台 |
| Manga-Availability-Finder | 搜索多个阅读平台的漫画/网络漫画可用性 |
| openbox-deals | 跨 8 个零售商的实时开箱和翻新优惠聚合器 |
| research-sentry | 扫描 ArXiv、PubMed 等的语音优先学术研究副驾驶 |
| restaurant-comparison-tool | 分析 Google Maps 评论、菜单和过敏原信号的餐前安全情报工具 |
| scholarship-finder | 从官方网站获取实时数据的 AI 驱动奖学金发现系统 |
| silicon-signal | 半导体供应链生命周期、可用性和交货期信号跟踪器 |
| stay-scout-hub | 为参加会议或活动旅行时搜索住宿地点 |

**加速器计划**:
TinyFish Accelerator 正在接受申请：$200万投资种子池、9周项目、免费额度、工程支持、商业指导。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Web Agent | SOTA Web Agent API | README | 高 |
| 自然语言 | 自然语言描述目标 | README | 高 |
| 浏览器自动化 | 真实浏览器自动化 | README | 高 |
| 隐身模式 | 代理轮换 + 隐身配置 | README | 高 |
| 多站点 | 跨多个网站并行处理 | README | 高 |
| 结构化输出 | 干净的 JSON 数据 | README | 高 |
| 生产日志 | 完整可观测性 | README | 高 |
| 20+ 示例 | 丰富的应用场景 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              TinyFish 架构                                   │
│           (Web Agent API)                                   │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              API 层                                │  │
│  │                                                  │  │
│  │   • HTTP API                                     │  │
│  │   • MCP 服务器 (Claude/Cursor)                  │  │
│  │   • Playground (可视化界面)                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Agent 核心层                          │  │
│  │                                                  │  │
│  │   • 自然语言理解                                 │  │
│  │   • 目标分解                                     │  │
│  │   • 步骤规划                                     │  │
│  │   • 执行引擎                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              浏览器层                                │  │
│  │                                                  │  │
│  │   • 真实浏览器 (非 headless)                     │  │
│  │   • 导航、表单、过滤器                           │  │
│  │   • 动态内容处理                                 │  │
│  │   • 多步骤流程                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              基础设施层                            │  │
│  │                                                  │  │
│  │   • 代理轮换                                     │  │
│  │   • 隐身配置                                     │  │
│  │   • 日志和可观测性                               │  │
│  │   • 错误处理和重试                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 示例食谱 | 各食谱目录/ | 实际应用场景示例 | 核心 |
| Anime | `anime-watch-hub/` | 动漫搜索 | 示例 |
| 电商 | `lego-hunter/`, `openbox-deals/` | 库存和价格 | 示例 |
| 研究 | `research-sentry/` | 学术研究 | 示例 |
| 金融 | `loan-decision-copilot/`, `silicon-signal/` | 金融数据 | 示例 |
| 工具 | `tinyskills/`, `skills/use-tinyfish/` | 技能和集成 | 工具 |

## 运行与开发方式

**使用 API**:
```bash
# HTTP API 调用
curl -X POST https://api.tinyfish.io/v1/run \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "goal": "Find the price of iPhone 16 on Amazon",
    "urls": ["https://amazon.com"]
  }'
```

**探索示例**:
```bash
# 克隆仓库
git clone https://github.com/tinyfish-io/tinyfish-cookbook.git
cd tinyfish-cookbook

# 查看具体食谱
cd lego-hunter/
# 阅读 README 和代码
```

**Playground**:
访问可视化 Playground 进行交互式探索

## 外部接口

**HTTP API**:
| 端点 | 功能 |
|------|------|
| `POST /v1/run` | 执行 Web Agent 任务 |
| `GET /v1/runs/:id` | 获取任务状态和结果 |
| `GET /v1/runs` | 列出历史任务 |

**MCP 服务器**:
支持 Claude/Cursor 的 Model Context Protocol

**响应格式**:
```json
{
  "status": "completed",
  "result": {
    "data": "...",
    "structured": true
  },
  "logs": [...]
}
```

## 数据流 / 控制流

```
用户请求 (自然语言 + URL)
    ↓
Agent 核心理解目标
    ↓
步骤规划
    ↓
浏览器执行 (导航、交互)
    ↓
数据提取和结构化
    ↓
JSON 响应
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Web Agent | 核心功能 | 高 |
| Browser Automation | 真实浏览器 | 高 |
| LLM | 自然语言理解 | 高 |
| Proxy Rotation | 隐身模式 | 高 |
| 多语言示例 | Python/JS/其他 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细 README，20+ 示例 | 高 |
| 上手难度 | 低 | HTTP API 调用简单 | 低 |
| 架构复杂度 | 高 | 完整 Web Agent 基础设施 | 高 |
| 外部依赖 | 中 | 依赖 TinyFish API | 中 |
| Stars | 中 | 1.4k stars | 中 |
| 维护状态 | 高 | 企业支持，活跃开发 | 高 |

**注意事项**:
- 需要 TinyFish API Key
- 商业使用需查看服务条款
- 加速器计划提供额外支持

**与竞品对比**:
| 指标 | TinyFish | Gemini | OpenAI | Anthropic |
|------|----------|--------|--------|-----------|
| Mind2Web | 90% | 69% | 61% | 56% |

## 关联概念

- [[Web-Agent]] - Web 自动化 Agent
- [[Browser-Automation]] - 浏览器自动化
- [[Mind2Web]] - Web Agent 基准测试
- [[Data-Extraction]] - 数据提取
- [[Price-Comparison]] - 价格比较
- [[Web-Scraping]] - 网页抓取

---

> 来源: [GitHub](https://github.com/tinyfish-io/tinyfish-cookbook) | 置信度: 基于 GitHub README
> 👤 **作者**: TinyFish
> ⭐ **Stars**: 1.4k
> 🔗 **官网**: [tinyfish.io](https://tinyfish.io)
> 📜 **许可证**: MIT
