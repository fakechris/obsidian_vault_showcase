---
title: "astonysh/OpenClaw-DeepReeder: OpenClaw智能阅读网关 (219 stars)"
github: "https://github.com/astonysh/OpenClaw-DeepReeder"
owner: astonysh
repo: OpenClaw-DeepReeder
date: 2026-02-26
batch_date: 2026-02-26
type: github-project
tags: [github, python, openclaw, reader, rss, ai, gateway]
pinboard_tags: [openclaw, reader, rss]
source_used: github-readme-extract
source_url: "https://github.com/astonysh/OpenClaw-DeepReeder"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# astonysh/OpenClaw-DeepReeder: OpenClaw智能阅读网关

## 一句话概述

专为OpenClaw生态系统设计的智能内容阅读网关，整合RSS订阅、文章抓取和AI摘要，实现自动化的信息流处理与知识沉淀。

## 项目定位

**目标用户**:
- 使用OpenClaw系统的知识工作者
- 需要自动化信息流处理的开发者
- 希望构建个人知识管理Pipeline的用户
- RSS重度使用者寻求AI增强方案

**解决的问题**:
- **信息过载**: RSS订阅源太多，无法逐一阅读
- **内容分散**: 文章分布在多个平台，难以统一管理
- **阅读效率低**: 长文阅读耗时，需要快速获取要点
- **知识沉淀难**: 阅读后的内容难以整理和回顾

**使用场景**:
- 每日RSS自动抓取和摘要
- 微信公众号文章批量处理
- 技术博客自动归档
- 与Obsidian/Notion等工具联动

**与同类项目差异**:
- **OpenClaw原生**: 与OpenClaw生态深度集成
- **多源聚合**: RSS + 微信公众号 + 网页抓取
- **AI驱动**: 内置LLM摘要和标签生成
- **双向同步**: 支持与Obsidian等工具的双向同步

## README 中文简介

**OpenClaw-DeepReeder** — 智能阅读网关

面向OpenClaw生态的内容处理Pipeline：
```
RSS源 / 公众号 / 网页 → 抓取 → AI摘要 → 知识库沉淀
```

**核心功能**:
- **RSS订阅管理**: 支持多源RSS订阅和抓取
- **智能抓取**: 适配微信公众号、知乎、Medium等平台
- **AI摘要**: 使用LLM生成文章要点
- **标签生成**: 自动提取关键词和主题标签
- **Obsidian集成**: 直接输出到Obsidian Vault

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| RSS抓取 | 多源RSS订阅和定时抓取 | README | 高 |
| 内容适配 | 微信公众号、知乎等反爬处理 | README | 高 |
| AI摘要 | LLM驱动的内容摘要 | README | 高 |
| 标签生成 | 自动关键词提取 | README | 高 |
| Obsidian导出 | 标准Markdown格式输出 | README | 高 |
| OpenClaw集成 | 与OpenClaw生态联动 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              OpenClaw-DeepReeder 架构                     │
│           (智能阅读网关)                                   │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              接口层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ RSS订阅      │ 公众号监听   │ 网页抓取     ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              处理层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ 内容抓取     │ 清洗         │ AI摘要       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输出层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Markdown     │ Obsidian     │ OpenClaw     ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录/文件 | 职责 | 关系 |
|------|----------|------|------|
| 主程序 | `main.py` | 入口和调度 | 核心 |
| RSS抓取 | `rss/` | RSS源管理 | 核心 |
| 内容适配 | `adapters/` | 平台特定抓取 | 核心 |
| AI处理 | `ai/` | 摘要和标签 | 核心 |
| 输出 | `exporters/` | 多格式导出 | 核心 |
| 配置 | `config.yaml` | 用户配置 | 配置 |

## 运行与开发方式

**安装**:

```bash
git clone https://github.com/astonysh/OpenClaw-DeepReeder.git
cd OpenClaw-DeepReeder
pip install -r requirements.txt
```

**配置**:
```yaml
# config.yaml
rss:
  sources:
    - url: "https://example.com/feed.xml"
      name: "Example Blog"

ai:
  provider: "openai"  # 或 "anthropic", "local"
  api_key: "your_key"
  model: "gpt-4o-mini"

output:
  format: "obsidian"
  path: "/path/to/vault/01-Inbox/"
```

**运行**:
```bash
# 单次运行
python main.py

# 定时运行（配合cron）
0 */6 * * * cd /path/to/OpenClaw-DeepReeder && python main.py
```

## 外部接口

**环境变量**:
| 变量 | 说明 |
|------|------|
| `OPENAI_API_KEY` | OpenAI API Key |
| `ANTHROPIC_API_KEY` | Claude API Key |
| `DEEPSEEK_API_KEY` | DeepSeek API Key |

**配置文件**:
- `config.yaml` - 主配置
- `sources.json` - RSS源列表

## 数据流 / 控制流

```
RSS/公众号/网页源
    ↓
定时抓取任务
    ↓
内容解析和清洗
    ↓
AI摘要生成
    ↓
标签和元数据提取
    ↓
Markdown格式输出
    ↓
Obsidian Vault / OpenClaw
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| feedparser | RSS解析 | 高 |
| BeautifulSoup | 网页抓取 | 高 |
| OpenAI/Anthropic API | LLM摘要 | 高 |
| PyYAML | 配置管理 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README简洁，有配置示例 | 中 |
| 上手难度 | 低 | pip安装，YAML配置 | 低 |
| 架构复杂度 | 中 | Pipeline架构 | 中 |
| 外部依赖 | 中 | 需要LLM API Key | 中 |
| Stars | 低 | 219 stars | 低 |
| 维护状态 | 中 | OpenClaw生态项目 | 中 |

**注意事项**:
- 需要配置LLM API Key
- 微信公众号抓取可能需要额外处理反爬
- 与OpenClaw生态绑定较深

## 关联概念

- [[OpenClaw]] - AI Agent生态系统
- [[RSS]] - 简易信息聚合
- [[Obsidian]] - 知识库工具
- [[LLM-Summarization]] - 大模型摘要
- [[WeChat-MP]] - 微信公众号
- [[Information-Gateway]] - 信息网关模式
- [[Knowledge-Pipeline]] - 知识处理Pipeline

---

> 来源: [GitHub](https://github.com/astonysh/OpenClaw-DeepReeder) | 置信度: 基于 GitHub README
> 👤 **作者**: astonysh
> ⭐ **Stars**: 219
> 🔗 **官网**: [GitHub](https://github.com/astonysh/OpenClaw-DeepReeder)
> 📜 **许可证**: MIT
