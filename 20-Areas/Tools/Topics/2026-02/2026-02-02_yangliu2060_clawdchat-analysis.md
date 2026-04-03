---
title: "yangliu2060/clawdchat-analysis: Moltbook AI社交网络分析 (89 stars)"
github: "https://github.com/yangliu2060/clawdchat-analysis"
owner: yangliu2060
repo: clawdchat-analysis
date: 2026-02-02
batch_date: 2026-02-02
type: github-project
tags: [github, openclaw-skill, moltbook, ai-social-network, analysis]
pinboard_tags: [openclaw-skill, moltbook]
source_used: github-readme-extract
source_url: "https://github.com/yangliu2060/clawdchat-analysis"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# yangliu2060/clawdchat-analysis: Moltbook AI社交网络分析

## 一句话概述

ClawdChat 是一个用于抓取和分析 Moltbook（AI agents 社交网络）的 Claude Code Skill，支持自动抓取 New + Top feeds、深度分析 Top 20 高价值帖子、智能提取问题和解决方案，并生成可视化每日报告。

## 项目定位

**目标用户**:
- 关注 AI agents 社交动态的研究者
- 需要追踪 Moltbook 平台热门话题的用户
- 想自动化获取 AI agents 讨论内容的开发者

**解决的问题**:
- **Moltbook 信息分散**: 需要手动浏览获取 AI agents 的讨论内容
- **高价值内容筛选**: 难以从大量帖子中识别核心问题和解决方案
- **内容分析耗时**: 人工分析帖子内容和评论效率低下
- **Spam 干扰**: 需要过滤低质量内容

**使用场景**:
- 每日自动抓取 Moltbook New 和 Top feeds
- 分析 AI agents 在讨论什么话题
- 提取有价值的解决方案和洞察
- 生成可视化日报

**与同类项目差异**:
- **专为 Moltbook 设计**: 针对 AI agents 社交网络优化
- **智能分析引擎**: 自动识别核心问题、提取解决方案、生成洞察
- **完善的 Spam 过滤**: 内置过滤规则保证内容质量
- **Claude Code Skill 形式**: 即装即用，自然语言触发

## README 中文简介

**ClawdChat** - Moltbook 深度分析 Skill for Claude Code

**功能**:
- 自动抓取 New + Top feeds（40-50 篇帖子）
- 深度抓取 Top 20 高价值帖子 + 评论
- 智能分析：问题识别、方案提取、洞察生成
- 生成可视化每日报告
- 完善的 Spam 过滤规则

**安装**:
```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/yangliu2060/clawdchat-analysis.git ~/.claude/skills/clawd
```

**使用**:
在 Claude Code 中输入以下任意触发词：

| 触发词 | 场景 |
|--------|------|
| clawdchat | 标准触发 |
| 抓取moltbook | 中文触发 |
| AI论坛分析 | 分析导向 |
| 今天AI们在讨论什么 | 问题导向 |

**输出示例**:
```
🦞 开始 Moltbook 深度分析...
✅ 访问首页，获取统计数据
153,222 AI agents | 17,902 posts | 197,184 comments
✅ 抓取 New Feed (20 篇)
✅ 抓取 Top Feed (20 篇)
✅ 去重后共 35 篇帖子
✅ 运行智能分析引擎
识别 8 个核心问题
提取 12 个解决方案
生成 4 个深度洞察
📄 报告已保存: ~/myassistant/chat/moltbook-daily/2026-01-31.md
```

**文件结构**:
```
clawdchat/
├── skill.md                    # 主 Skill 文件
├── references/
│   ├── selectors.md            # 页面选择器参考
│   └── spam-rules.md           # Spam 过滤规则
└── README.md
```

**依赖**:
- Claude Code with Playwright MCP（用于浏览器自动化）

**作者**: smith铜匠

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Moltbook 抓取 | 自动抓取 New + Top feeds | README | 高 |
| 智能分析引擎 | 问题识别、方案提取、洞察生成 | README | 高 |
| Spam 过滤 | 完善的过滤规则 | README | 高 |
| 每日报告 | 生成可视化 markdown 报告 | README | 高 |
| Claude Code Skill | 自然语言触发 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              ClawdChat 系统架构                           │
│           (Moltbook AI社交网络分析)                         │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              触发层                              │  │
│  │                                                  │  │
│  │   触发词:                                        │  │
│  │   - clawdchat                                    │  │
│  │   - 抓取moltbook                                 │  │
│  │   - AI论坛分析                                   │  │
│  │   - 今天AI们在讨论什么                           │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              抓取层                              │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │   New Feed   │    │   Top Feed   │        │  │
│  │   │  (20 篇)     │    │  (20 篇)     │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  │   深度抓取: Top 20 高价值帖子 + 评论           │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              处理层                              │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │    去重     │    │  Spam 过滤   │        │  │
│  │   │             │    │  (rules)     │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              分析层                              │  │
│  │                                                  │  │
│  │   智能分析引擎:                                  │  │
│  │   - 识别核心问题                                 │  │
│  │   - 提取解决方案                                 │  │
│  │   - 生成深度洞察                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输出层                              │  │
│  │                                                  │  │
│  │   📄 每日报告: ~/myassistant/chat/moltbook-daily/ │  │
│  │      YYYY-MM-DD.md                              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 文件 | 职责 | 关系 |
|------|------|------|------|
| 主 Skill | `skill.md` | Skill 定义和逻辑 | 核心 |
| 选择器参考 | `references/selectors.md` | 页面 DOM 选择器 | 抓取配置 |
| Spam 规则 | `references/spam-rules.md` | 过滤规则 | 质量控制 |

## 运行与开发方式

**安装**:
```bash
git clone https://github.com/yangliu2060/clawdchat-analysis.git ~/.claude/skills/clawd
```

**依赖**:
- Claude Code
- Playwright MCP（浏览器自动化）

**使用**:
在 Claude Code 中输入触发词即可：
```
clawdchat
# 或
抓取moltbook
# 或
AI论坛分析
# 或
今天AI们在讨论什么
```

**输出位置**:
`~/myassistant/chat/moltbook-daily/YYYY-MM-DD.md`

## 外部接口

**触发词**:
| 触发词 | 语言 | 用途 |
|--------|------|------|
| clawdchat | 英文 | 标准触发 |
| 抓取moltbook | 中文 | 直接表达 |
| AI论坛分析 | 中文 | 分析导向 |
| 今天AI们在讨论什么 | 中文 | 问题导向 |

**输出格式**:
- Markdown 报告
- 包含统计数据、抓取内容、分析结果

## 数据流 / 控制流

```
用户触发 (自然语言)
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 访问 Moltbook 首页                                       │
│    - 获取统计数据: AI agents 数、posts 数、comments 数     │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. 抓取 Feeds                                              │
│    - New Feed: 20 篇                                      │
│    - Top Feed: 20 篇                                      │
│    - 深度抓取 Top 20 高价值帖子 + 评论                    │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 内容处理                                                │
│    - 去重                                                  │
│    - Spam 过滤 (基于 rules)                               │
│    - 保留高质量内容                                       │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 4. 智能分析                                                │
│    - 识别 N 个核心问题                                    │
│    - 提取 N 个解决方案                                    │
│    - 生成 N 个深度洞察                                    │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 5. 生成报告                                                │
│    - Markdown 格式                                        │
│    - 可视化展示                                          │
│    - 保存到 ~/myassistant/chat/moltbook-daily/          │
└────────────────────────────────────────────────────────────┘
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Claude Code Skill | 项目类型 | 高 |
| Playwright MCP | 浏览器自动化 | 高 |
| Markdown | 报告格式 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 简洁，功能描述清晰 | 中 |
| 上手难度 | 低 | git clone 即装即用 | 低 |
| 架构复杂度 | 低 | Skill 形式，逻辑简单 | 低 |
| 外部依赖 | 中 | 依赖 Moltbook 平台 | 中 |
| Stars | 低 | 89 stars |
| 维护风险 | 中 | 依赖 Moltbook 平台变化 | 中 |

**注意事项**:
- 需要 Playwright MCP 支持
- 依赖 Moltbook 平台，网站变化可能影响抓取
- Spam 规则需要持续更新

## 关联概念

- [[Claude-Code-Skills]] - Claude Code Skill 系统
- [[Moltbook]] - AI agents 社交网络
- [[Playwright-MCP]] - Playwright Model Context Protocol
- [[Web-Scraping]] - 网页抓取

---

> 来源: [GitHub](https://github.com/yangliu2060/clawdchat-analysis) | 置信度: 基于 GitHub README
> 👤 **作者**: yangliu2060 (smith铜匠)
> ⭐ **Stars**: 89
> 🔗 **平台**: [Moltbook](https://moltbook.com)
