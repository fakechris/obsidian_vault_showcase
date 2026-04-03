---
title: "vigorX777/ai-daily-digest: AI日报生成工具 (1.5k stars)"
github: "https://github.com/vigorX777/ai-daily-digest"
owner: vigorX777
repo: ai-daily-digest
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, typescript, ai, rss, newsletter, hackernews]
pinboard_tags: [ai, rss, newsletter]
source_used: github-readme-extract
source_url: "https://github.com/vigorX777/ai-daily-digest"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# vigorX777/ai-daily-digest: AI日报生成工具

## 一句话概述

从 Andrej Karpathy 推荐的90个Hacker News顶级技术博客抓取最新文章，通过AI多维评分筛选，生成结构化每日精选日报，支持Gemini和OpenAI兼容API。

## 项目定位

**目标用户**:
- 需要每日技术资讯的技术从业者
- 希望自动化信息筛选的读者
- 关注AI/ML、安全、工程领域的开发者
- 需要中文技术日报的用户

**解决的问题**:
- **信息过载**: 技术博客太多，无法一一阅读
- **筛选困难**: 难以快速识别高质量文章
- **语言障碍**: 英文内容阅读效率低
- **手动整理**: 制作日报耗时费力

**使用场景**:
- 每日晨间技术资讯阅读
- 团队技术分享素材收集
- 个人知识管理自动化
- 技术趋势跟踪

**与同类项目差异**:
- **精选信源**: 来自Hacker News社区最受欢迎的90个独立技术博客
- **AI多维评分**: 相关性、质量、时效性三维度打分
- **中英双语**: 标题自动翻译，保留原文链接
- **结构化摘要**: 4-6句完整概述，非一句话敷衍
- **趋势洞察**: 归纳当日技术圈宏观趋势

## README 中文简介

**AI Daily Digest** - AI评分筛选的技术日报生成器

从 Andrej Karpathy 推荐的 90 个 Hacker News 顶级技术博客中抓取最新文章，通过 AI 多维评分筛选，生成一份结构化的每日精选日报。

**核心特性**:
- **零依赖**: 纯 TypeScript 单文件，基于 Bun 原生 fetch 和内置 XML 解析
- **五步流水线**: RSS抓取 → 时间过滤 → AI评分+分类 → AI摘要+翻译 → 趋势总结
- **六大分类**: AI/ML、安全、工程、工具/开源、观点/杂谈、其他
- **智能降级**: Gemini优先，失败自动降级到OpenAI兼容API
- **配置记忆**: API Key和偏好参数自动持久化

**使用方式**:

作为 OpenCode Skill 使用:
```
/digest
```

命令行运行:
```bash
export GEMINI_API_KEY="your-key"
npx -y bun scripts/digest.ts --hours 48 --top-n 15 --lang zh --output ./digest.md
```

**日报结构**:
- 📝 今日看点 - 3-5句话宏观趋势总结
- 🏆 今日必读 - Top 3深度展示（中英双语标题、摘要、推荐理由）
- 📊 数据概览 - 统计表格 + Mermaid图表 + 话题标签云
- 分类文章列表 - 按6大分类分组

**信息源**:
90个RSS源精选自Hacker News社区最受欢迎的独立技术博客，包括 Simon Willison、Paul Graham、Dan Abramov、Gwern、Krebs on Security等。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| RSS抓取 | 并发抓取90个源（10路并发，15s超时） | README | 高 |
| AI评分 | 相关性/质量/时效性三维度打分（1-10） | README | 高 |
| 智能分类 | 自动归入6大类别 | README | 高 |
| 中英双语 | 标题自动翻译为中文 | README | 高 |
| 趋势总结 | AI归纳当日技术圈宏观趋势 | README | 高 |
| API降级 | Gemini失败自动降级OpenAI兼容接口 | README | 高 |
| 可视化 | Mermaid图表 + ASCII柱状图 + 标签云 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              AI Daily Digest 架构                           │
│           (AI日报生成工具)                                  │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输入层                                │  │
│  │                                                  │  │
│  │   • 90个Hacker News顶级博客RSS源                 │  │
│  │   • RSS 2.0 / Atom 格式兼容                      │  │
│  │   • 10路并发抓取（15s超时）                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              处理流水线                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ RSS抓取      │ 时间过滤     │ AI评分      ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ AI摘要+翻译  │ 趋势总结     │ 报告生成    ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输出层                                │  │
│  │                                                  │  │
│  │   • Markdown日报文件                             │  │
│  │   • Mermaid图表（分类/关键词）                   │  │
│  │   • ASCII柱状图（终端友好）                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 文件 | 职责 | 关系 |
|------|------|------|------|
| 核心脚本 | `scripts/digest.ts` | 完整流水线逻辑 | 核心 |
| Skill定义 | `SKILL.md` | OpenCode Skill配置 | 扩展 |
| 资源文件 | `assets/` | 静态资源 | 辅助 |
| 示例输出 | `scripts/` | 脚本和配置 | 工具 |

## 运行与开发方式

**快速开始**:
```bash
# 设置API Key
export GEMINI_API_KEY="your-key"

# 运行（通过npx自动安装Bun）
npx -y bun scripts/digest.ts --hours 48 --top-n 15 --lang zh --output ./digest.md
```

**OpenCode Skill**:
```
/digest
# 交互式选择：时间范围、精选数量、输出语言
```

**配置持久化**:
配置文件自动保存到 `~/.hn-daily-digest/config.json`

**切换AI提供商**:
支持修改 `scripts/digest.ts` 替换为:
- OpenAI: `https://api.openai.com/v1/chat/completions`
- Anthropic: `https://api.anthropic.com/v1/messages`
- DeepSeek: `https://api.deepseek.com/v1/chat/completions`

## 外部接口

**CLI参数**:
| 参数 | 说明 | 默认值 |
|------|------|--------|
| `--hours` | 时间范围（24h/48h/72h/7天） | 48h |
| `--top-n` | 精选数量（10/15/20） | 15 |
| `--lang` | 输出语言（zh/en） | zh |
| `--output` | 输出文件路径 | ./digest.md |

**环境变量**:
| 变量 | 说明 |
|------|------|
| `GEMINI_API_KEY` | Gemini API密钥 |
| `OPENAI_API_KEY` | OpenAI兼容API密钥（可选） |
| `OPENAI_API_BASE` | 自定义API端点（可选） |
| `OPENAI_MODEL` | 自定义模型（可选） |

**六大分类体系**:
| 分类 | 覆盖范围 |
|------|----------|
| 🤖 AI/ML | AI、机器学习、LLM、深度学习 |
| 🔒 安全 | 安全、隐私、漏洞、加密 |
| ⚙️ 工程 | 软件工程、架构、编程语言 |
| 🛠 工具/开源 | 开发工具、开源项目、新框架 |
| 💡 观点/杂谈 | 行业观点、个人思考、职业发展 |
| 📝 其他 | 不属于以上内容 |

## 数据流 / 控制流

```
90个RSS源
    ↓
并发抓取（10路）
    ↓
时间窗口筛选
    ↓
AI多维评分（相关性/质量/时效性）
    ↓
Top N文章筛选
    ↓
AI摘要生成 + 中文翻译
    ↓
趋势总结归纳
    ↓
Markdown报告生成（含Mermaid图表）
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 | 高 |
| Bun | 运行时 | 高 |
| Gemini API | 默认AI后端 | 高 |
| OpenAI兼容API | 降级方案 | 高 |
| RSS/Atom | 信息源格式 | 高 |
| Mermaid | 图表生成 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，含中文 | 高 |
| 上手难度 | 低 | 一行命令运行 | 低 |
| 架构复杂度 | 低 | 单文件脚本 | 低 |
| 外部依赖 | 中 | 需要AI API密钥 | 中 |
| Stars | 中 | 1.5k stars | 中 |
| 维护状态 | 高 | 活跃开发 | 高 |

**注意事项**:
- 需要Gemini API Key（免费获取）或OpenAI兼容API
- 依赖Hacker News博客RSS源可用性
- 中文翻译质量取决于AI模型

**推荐信源**:
- Simon Willison (simonwillison.net)
- Paul Graham (paulgraham.com)
- Dan Abramov (overreacted.io)
- Gwern (gwern.net)
- Krebs on Security (krebsonsecurity.com)
- Antirez (antirez.com)

## 关联概念

- [[Hacker-News]] - Hacker News技术社区
- [[RSS]] - Really Simple Syndication
- [[Andrej-Karpathy]] - 知名AI研究者
- [[Gemini-API]] - Google Gemini API
- [[OpenAI-Compatible-API]] - OpenAI兼容API格式
- [[Mermaid]] - 图表生成工具
- [[Bun]] - JavaScript运行时
- [[OpenCode-Skill]] - OpenCode技能系统

---

> 来源: [GitHub](https://github.com/vigorX777/ai-daily-digest) | 置信度: 基于 GitHub README
> 👤 **作者**: vigorX777
> ⭐ **Stars**: 1.5k
> 🔗 **官网**: [GitHub](https://github.com/vigorX777/ai-daily-digest)
> 📜 **许可证**: 未明确
