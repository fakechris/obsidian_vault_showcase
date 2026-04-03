---
title: "virattt/dexter: 自主金融研究 Agent (20.8k stars)"
github: "https://github.com/virattt/dexter"
owner: virattt
repo: dexter
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, ai-agent, financial-research, autonomous, typescript, llm, trading]
pinboard_tags: [agent, finance, research]
source_used: github-readme-extract
source_url: "https://github.com/virattt/dexter"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# virattt/dexter: 自主金融研究 Agent

## 一句话概述

Dexter 是一个自主金融研究 Agent，将复杂金融问题分解为结构化研究计划，使用实时市场数据自主执行分析任务，通过自我验证和迭代优化，生成数据支持的可靠答案——专为金融研究打造的类 Claude Code 工具。

## 项目定位

**目标用户**:
- 金融分析师和投资研究人员
- 量化交易员和投资组合经理
- 需要深度金融数据分析的投资者
- 对金融 AI Agent 感兴趣的开发者

**解决的问题**:
- **金融研究耗时**: 传统金融分析需要大量手动数据收集和处理
- **信息过载**: 金融市场数据庞杂，难以快速提取关键洞察
- **分析不一致**: 人工分析可能存在偏差和不一致
- **实时性需求**: 市场变化快速，需要及时的数据和分析

**使用场景**:
- 深度个股研究和财务分析
- 行业趋势和市场动态追踪
- 财报数据分析和对比
- 投资组合研究和风险评估
- 自动化金融数据采集

**与同类项目差异**:
- **专为金融设计**: 专注于金融研究，而非通用对话
- **任务规划**: 自动将复杂查询分解为结构化研究步骤
- **自我验证**: 检查结果并迭代直到任务完成
- **实时数据**: 接入实时财务报表和市场数据
- **安全意识**: 内置循环检测和步骤限制防止失控

## README 中文简介

**Dexter** 🤖 - 为金融而生的自主研究 Agent

Dexter 像一个会思考、计划和学习的 Claude Code，专门用于金融研究。它将复杂金融问题转化为清晰的、分步骤的研究计划，使用实时市场数据运行任务，自我检查工作，并持续优化结果直到获得有数据支持的可靠答案。

**核心能力**:
- **智能任务规划**: 自动将复杂查询分解为结构化研究步骤
- **自主执行**: 选择并执行正确的工具收集金融数据
- **自我验证**: 检查自己的工作并迭代直到完成
- **实时金融数据**: 访问利润表、资产负债表和现金流量表
- **安全特性**: 内置循环检测和步骤限制防止失控执行

**技术栈**:
- TypeScript
- Bun 运行时
- OpenAI/Anthropic/Google/XAI API
- Financial Datasets API
- Exa/Tavily Web 搜索
- LangSmith 评估追踪

**快速开始**:

```bash
# 克隆仓库
git clone https://github.com/virattt/dexter.git
cd dexter

# 安装依赖 (需要 Bun)
bun install

# 配置环境变量
cp env.example .env
# 编辑 .env 添加 API keys

# 启动交互模式
bun start

# 或开发模式
bun dev
```

**API 需求**:
- OpenAI API key (必需)
- Financial Datasets API key (必需，AAPL/NVDA/MSFT 免费)
- Exa API key (可选，网页搜索)

**示例查询**:
- "分析特斯拉过去5年的盈利能力趋势"
- "比较苹果和微软的财务健康状况"
- "评估亚马逊的现金流生成能力"
- "研究半导体行业的增长前景"

**评估套件**:
Dexter 包含评估套件，使用 LangSmith 追踪和 LLM-as-judge 评分。

```bash
# 运行所有评估
bun run src/evals/run.ts

# 随机采样评估
bun run src/evals/run.ts --sample 10
```

**调试追踪**:
所有工具调用记录到 `.dexter/scratchpad/` 目录的 JSONL 文件：
- `init`: 原始查询
- `tool_result`: 每次工具调用及结果
- `thinking`: Agent 推理步骤

**WhatsApp 集成**:
```bash
# 链接 WhatsApp 账号
bun run gateway:login

# 启动网关
bun run gateway
```
然后给自己的 WhatsApp 发送消息即可与 Dexter 对话。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 任务规划 | 自动分解复杂查询 | README | 高 |
| 财务数据 | 实时财务报表 | README | 高 |
| 自主执行 | 选择和执行工具 | README | 高 |
| 自我验证 | 检查结果并迭代 | README | 高 |
| 循环检测 | 防止执行失控 | README | 高 |
| 评估套件 | LLM-as-judge 评分 | README | 高 |
| 调试追踪 | 详细调用日志 | README | 高 |
| WhatsApp | 聊天界面集成 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Dexter 架构                                   │
│           (自主金融研究 Agent)                              │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              用户接口层                            │  │
│  │                                                  │  │
│  │   • CLI 交互模式                                 │  │
│  │   • WhatsApp 网关                                │  │
│  │   • API 接口                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Agent 核心层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┐ ┌──────────────┐              │  │
│  │   │ 任务规划器   │ │ 执行引擎     │              │  │
│  │   │              │ │              │              │  │
│  │   │ • 查询分解   │ │ • 工具选择   │              │  │
│  │   │ • 步骤生成   │ │ • 调用执行   │              │  │
│  │   │ • 依赖分析   │ │ • 结果处理   │              │  │
│  │   └──────────────┘ └──────────────┘              │  │
│  │                                                  │  │
│  │   ┌──────────────┐ ┌──────────────┐              │  │
│  │   │ 自我验证器   │ │ 循环检测器   │              │  │
│  │   │              │ │              │              │  │
│  │   │ • 结果检查   │ │ • 步骤计数   │              │  │
│  │   │ • 置信度评估 │ │ • 模式检测   │              │  │
│  │   │ • 迭代决策   │ │ • 超时保护   │              │  │
│  │   └──────────────┘ └──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              工具层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐ │  │
│  │   │ 财务数据 API │ 网页搜索     │ LLM 推理     │ │  │
│  │   │              │              │              │ │  │
│  │   │ • 利润表     │ • Exa        │ • OpenAI     │ │  │
│  │   │ • 资产负债表 │ • Tavily   │ • Anthropic  │ │  │
│  │   │ • 现金流量表 │              │ • Google     │ │  │
│  │   └──────────────┴──────────────┴──────────────┘ │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              数据层                                │  │
│  │                                                  │  │
│  │   • Scratchpad (调试日志)                        │  │
│  │   • LangSmith (追踪)                             │  │
│  │   • 评估数据集                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| Agent 核心 | src/ | 任务规划和执行 | 核心 |
| 工具集 | src/tools/ | 财务数据和搜索 | 核心 |
| 评估 | src/evals/ | 测试和评分 | 质量 |
| WhatsApp | gateway/ | 聊天接口 | 接口 |
| 配置 | env | API 密钥管理 | 配置 |

## 运行与开发方式

**环境要求**:
- Bun 运行时 (v1.0+)
- OpenAI API key
- Financial Datasets API key

**安装**:
```bash
# 安装 Bun
curl -fsSL https://bun.com/install | bash

# 克隆和安装
git clone https://github.com/virattt/dexter.git
cd dexter
bun install

# 配置环境
cp env.example .env
# 编辑 .env
```

**运行**:
```bash
# 交互模式
bun start

# 开发模式 (热重载)
bun dev

# 评估
bun run src/evals/run.ts
bun run src/evals/run.ts --sample 10
```

**WhatsApp 模式**:
```bash
# 首次登录
bun run gateway:login

# 启动网关
bun run gateway
```

## 外部接口

**CLI**:
| 命令 | 功能 |
|------|------|
| `bun start` | 交互模式 |
| `bun dev` | 开发模式 |
| `bun run gateway` | WhatsApp 网关 |

**API 集成**:
| 服务 | 用途 |
|------|------|
| OpenAI | LLM 推理 |
| Anthropic | Claude 模型 (可选) |
| Google | Gemini 模型 (可选) |
| XAI | Grok 模型 (可选) |
| Financial Datasets | 财务数据 |
| Exa/Tavily | 网页搜索 |
| LangSmith | 追踪和评估 |

**数据结构 (Scratchpad)**:
```typescript
{
  type: "tool_result",
  timestamp: "...",
  toolName: "get_income_statements",
  args: {...},
  result: {...},
  llmSummary: "..."
}
```

## 数据流 / 控制流

```
用户查询
    ↓
任务规划器 (分解为步骤)
    ↓
执行引擎 (选择工具)
    ↓
工具调用 (财务 API / 搜索)
    ↓
结果处理 (LLM 总结)
    ↓
自我验证 (检查完成度)
    ↓
┌────────────────┐
│ 完成?          │
└────────────────┘
    ↓ 是              ↓ 否
输出结果          继续迭代
    ↓
记录到 Scratchpad
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (99.4%) | 高 |
| Bun | 运行时 | 高 |
| Jest | 测试 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README 详细 | 高 |
| 上手难度 | 中 | 需要 API keys | 中 |
| 架构复杂度 | 中 | Agent 架构 | 中 |
| 外部依赖 | 高 | 依赖多个 API | 高 |
| Stars | 高 | 20.8k stars | 高 |
| 活跃状态 | 高 | 活跃开发 | 高 |

**注意事项**:
- 需要多个 API key，配置较复杂
- 金融数据 API 可能需要付费
- LLM 调用成本需监控
- 生产使用需验证结果准确性

## 关联概念

- [[Claude-Code]] - Anthropic CLI 编码工具
- [[Financial-AI]] - 金融 AI 应用
- [[Agent-Architecture]] - Agent 架构设计
- [[LLM-as-Judge]] - LLM 评估模式
- [[Quantitative-Research]] - 量化研究

---

> 来源: [GitHub](https://github.com/virattt/dexter) | 置信度: 基于 GitHub README
> 👤 **作者**: virattt
> ⭐ **Stars**: 20.8k
> 📜 **许可证**: MIT
