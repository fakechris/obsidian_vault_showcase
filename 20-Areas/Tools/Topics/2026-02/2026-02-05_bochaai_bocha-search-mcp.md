---
title: "BochaAI/bocha-search-mcp: 博查中文搜索 MCP 服务器 (154 stars)"
github: "https://github.com/BochaAI/bocha-search-mcp"
owner: BochaAI
repo: bocha-search-mcp
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, mcp, search-engine, chinese, api, python, deepseek]
pinboard_tags: [mcp, search, chinese-api]
source_used: github-readme-extract
source_url: "https://github.com/BochaAI/bocha-search-mcp"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# BochaAI/bocha-search-mcp: 博查中文搜索 MCP 服务器

## 一句话概述

博查 MCP 服务器是一个给 AI 用的中文搜索引擎，让 AI 应用从近百亿网页和生态内容源中获取高质量世界知识，支持网页搜索和 AI 搜索两种模式，已服务 3000+ 企业用户，成为国内 60% 以上 AI 应用的联网搜索供应商。

## 项目定位

**目标用户**:
- 需要为 AI 应用添加联网搜索能力的开发者
- 使用 Claude、Cursor 等 MCP 客户端的用户
- 需要中文搜索 API 的企业和开发者
- 构建 RAG、Agent 系统的工程师

**解决的问题**:
- **AI 知识局限**: 大模型缺乏实时信息和最新知识
- **中文搜索质量**: 传统搜索引擎不适合 AI 场景
- **Bing API 限制**: 海外数据、价格昂贵、不提供文本摘要
- **内容生态**: 需要覆盖天气、新闻、百科、医疗等多领域

**使用场景**:
- AI 助手实时回答时效性问题
- RAG 系统获取外部知识
- Agent 工具调用搜索功能
- 企业知识库补充实时信息

**与同类项目差异**:
- **专为 AI 设计**: 基于语义排序，大模型更喜欢
- **国内领先**: 国内最接近 Bing Search API 的搜索引擎
- **价格合理**: 比 Bing API (15美元/千次) 更优惠
- **内容丰富**: 近百亿网页 + 生态合作内容(短视频、新闻、百科等)
- **模态卡支持**: 天气、百科、医疗等几十种结构化数据

## README 中文简介

**博查 MCP 服务器** - 给 AI 用的搜索引擎

**产品描述**:
博查是一个给 AI 用的搜索引擎，让你的 AI 应用从近百亿网页和生态内容源中获取高质量的世界知识，涵盖天气、新闻、百科、医疗、火车票、图片等多种领域。

**核心工具**:

**Tool1: Bocha Web Search**
- **功能**: 从博查搜索全网信息和网页链接
- **返回**: 网页标题、URL、摘要、网站名称、图标、发布时间、图片链接
- **参数**:
  - `query`: 搜索词(必填)
  - `freshness`: 时间范围(YYYY-MM-DD、oneYear、oneMonth、oneWeek、oneDay，默认 noLimit)
  - `count`: 返回条数(1-50，默认 10)

**Tool2: Bocha AI Search**
- **功能**: 在网页搜索基础上，AI 识别语义并返回垂直领域结构化模态卡
- **模态卡类型**: 天气卡、日历卡、百科卡、医疗卡、火车票卡、股票卡等几十种
- **优势**: 语义识别更准确、时效性更好、内容更丰富
- **参数**: 同 Web Search

**安装部署**:

**步骤一**: 下载代码
```bash
git clone git@github.com:BochaAI/bocha-search-mcp.git
```

**步骤二**: 在 Claude Desktop 中配置

macOS:
```json
{
  "mcpServers": {
    "bocha-search-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/bocha-search-mcp",
        "run",
        "bocha-search-mcp"
      ],
      "env": {
        "BOCHA_API_KEY": "sk-****"
      }
    }
  }
}
```

Windows: `%APPDATA%/Claude/claude_desktop_config.json`

**步骤三**: 获取 API Key
前往 [博查 AI 开放平台](https://bocha-ai.com) 登录后获取 API Key

**步骤四**: 调试(可选)
```bash
npx @modelcontextprotocol/inspector uv --directory /path/to/bocha-search-mcp run bocha-search-mcp
```

**客户案例**:
目前博查已服务 3000+ 企业用户和 20000+ 开发者用户，并且成为 DeepSeek 官方联网搜索供应商以及阿里、腾讯、字节官方推荐的搜索 API。

**内容源**:
- 全网近百亿个网页
- 生态合作内容: 短视频、新闻、百科、天气、医疗、火车票、酒店、餐厅、景点、企业、学术等

**技术优势**:
- 基于多模态混合搜索与语义排序技术
- 支持 AI 应用场景的自然语言搜索
- 提供干净、准确、高质量的答案
- 语义排序基于 Transformer 架构，与大模型同架构

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 网页搜索 | 全网通用搜索，返回标题/URL/摘要/时间等 | README | 高 |
| AI 搜索 | 语义识别 + 结构化模态卡 | README | 高 |
| 时间过滤 | 支持多种时间范围筛选 | README | 高 |
| 多平台适配 | 方舟、Python、Claude、Cursor 等 | README | 高 |
| 垂直领域 | 天气、新闻、百科、医疗、火车票等 | README | 高 |
| 语义排序 | Transformer 架构，大模型更偏好 | README | 高 |
| 大规模服务 | 3000+ 企业，20000+ 开发者 | README | 高 |
| DeepSeek 官方 | DeepSeek 官方联网搜索供应商 | README | 高 |
| MCP 协议 | 标准 MCP 服务器实现 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              博查 MCP 服务器架构                            │
│           (中文 AI 搜索引擎 MCP 服务)                       │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              MCP 协议层                            │  │
│  │                                                  │  │
│  │   • 标准 MCP 服务器实现                          │  │
│  │   • tools/call 接口                              │  │
│  │   • uv 运行时封装                                │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              搜索服务层 (Python)                   │  │
│  │                                                  │  │
│  │   ┌──────────────┐ ┌──────────────┐            │  │
│  │   │ Web Search   │ │  AI Search   │            │  │
│  │   │              │ │              │            │  │
│  │   │ • 全网搜索   │ │ • 语义识别   │            │  │
│  │   │ • 网页信息   │ │ • 模态卡     │            │  │
│  │   │ • 时效过滤   │ │ • 结构化数据 │            │  │
│  │   └──────────────┘ └──────────────┘            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              博查搜索引擎 API                    │  │
│  │                                                  │  │
│  │   • 近百亿网页索引                               │  │
│  │   • 多模态混合搜索                               │  │
│  │   • Transformer 语义排序                         │  │
│  │   • 生态内容源整合                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| MCP 入口 | `src/bocha_search_mcp/` | MCP 协议实现 | 入口 |
| Web Search | `src/bocha_search_mcp/` | 网页搜索工具 | 核心功能 |
| AI Search | `src/bocha_search_mcp/` | AI 搜索工具 | 核心功能 |
| 配置 | `.env.example` | API Key 配置 | 配置 |

## 运行与开发方式

**快速开始**:
```bash
# 克隆仓库
git clone git@github.com:BochaAI/bocha-search-mcp.git
cd bocha-search-mcp

# 配置环境变量
cp .env.example .env
# 编辑 .env 添加 BOCHA_API_KEY

# 使用 uv 运行
uv run bocha-search-mcp
```

**Claude Desktop 配置**:
```json
{
  "mcpServers": {
    "bocha-search-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/bocha-search-mcp",
        "run",
        "bocha-search-mcp"
      ],
      "env": {
        "BOCHA_API_KEY": "your-api-key"
      }
    }
  }
}
```

**调试**:
```bash
npx @modelcontextprotocol/inspector \
  uv --directory /path/to/bocha-search-mcp run bocha-search-mcp
```

## 外部接口

**MCP Tools**:
| 工具名 | 功能 | 参数 |
|--------|------|------|
| `Bocha Web Search` | 全网网页搜索 | query, freshness, count |
| `Bocha AI Search` | 语义搜索+模态卡 | query, freshness, count |

**参数说明**:
| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `query` | string | 是 | 搜索词 |
| `freshness` | string | 否 | 时间范围: noLimit/oneYear/oneMonth/oneWeek/oneDay 或日期 |
| `count` | integer | 否 | 返回条数 1-50，默认 10 |

**输出字段**:
| 字段 | 说明 |
|------|------|
| 网页标题 | 搜索结果标题 |
| 网页链接 | 结果 URL |
| 网页摘要 | 内容摘要 |
| 发布时间 | 文章发布时间 |
| 网站名称 | 来源网站 |
| 模态卡 | AI Search 特有，结构化数据卡 |

**支持平台**:
- 方舟
- Python
- Claude Desktop
- Cursor

## 数据流 / 控制流

```
用户提问 (时效性问题)
    ↓
AI 判断需要搜索
    ↓
调用 Bocha Web/AI Search MCP
    ↓
博查搜索引擎处理
    ├─ 多模态混合搜索
    ├─ Transformer 语义排序
    └─ 模态卡识别(如需要)
    ↓
返回搜索结果
    ├─ 网页标题/URL/摘要
    └─ 结构化模态卡(AI Search)
    ↓
AI 整合结果生成回答
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | MCP 服务主要语言 (100%) | 高 |
| MCP 协议 | Model Context Protocol | 高 |
| uv | Python 包管理/运行 | 高 |
| Transformer | 语义排序架构 | 高 |
| 博查 API | 搜索引擎后端 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | 基础 README，部分细节需补充 | 中 |
| 上手难度 | 低 | 标准 MCP 配置流程 | 低 |
| 架构复杂度 | 低 | MCP 封装 + API 调用 | 低 |
| 外部依赖 | 中 | 依赖博查 API 服务 | 中 |
| Stars | 低 | 154 stars | 低 |
| 服务规模 | 高 | 3000+ 企业，DeepSeek 官方 | 高 |

**注意事项**:
- 需要博查 AI 开放平台 API Key
- 国内服务，适合中文场景
- 有免费额度，商业使用需了解定价
- 模态卡类型持续增加中

## 关联概念

- [[MCP]] - Model Context Protocol
- [[Search-API]] - 搜索 API 服务
- [[RAG]] - Retrieval-Augmented Generation
- [[Semantic-Search]] - 语义搜索技术
- [[DeepSeek]] - DeepSeek AI 模型
- [[Chinese-Search]] - 中文搜索引擎

---

> 来源: [GitHub](https://github.com/BochaAI/bocha-search-mcp) | 置信度: 基于 GitHub README
> 👤 **作者**: BochaAI
> ⭐ **Stars**: 154
> 🔗 **官网**: [博查 AI 开放平台](https://bocha-ai.com)
