---
title: "0smboy/rss-swipr: Tinder 风格 RSS 阅读器 (4 stars)"
github: "https://github.com/0smboy/rss-swipr"
owner: 0smboy
repo: rss-swipr
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, python, rss, reader, ml, swipe]
pinboard_tags: [rss, reader, python]
source_used: github-readme-extract
source_url: "https://github.com/0smboy/rss-swipr"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# 0smboy/rss-swipr: Tinder 风格 RSS 阅读器

## 一句话概述

RSS Swipr 是一个支持本地偏好学习的 Tinder 风格 RSS 阅读器，卡片式滑动交互，可根据用户喜好训练推荐模型，支持移动端优先体验和桌面端控制。

## 项目定位

**目标用户**:
- 喜欢 Tinder 风格交互的 RSS 用户
- 希望个性化 RSS 推荐的读者
- 需要移动端友好 RSS 应用的用户
- 对 ML 推荐系统感兴趣的开发者

**解决的问题**:
- **传统 RSS 阅读器枯燥**: 列表式阅读缺乏趣味性
- **信息过载**: RSS 订阅源过多难以筛选
- **缺乏个性化**: 传统 RSS 按时间排序，无智能推荐
- **移动端体验差**: 多数 RSS 应用对移动设备不友好
- **无本地学习**: 用户偏好难以在本地记录和训练

**使用场景**:
- 日常新闻阅读
- 博客文章筛选
- 个性化内容发现
- 机器学习推荐实验

**与同类项目差异**:
- **Tinder 风格**: 滑动卡片式交互
- **本地偏好学习**: 滑动/投票训练个性化模型
- **移动优先**: 移动端优化体验
- **模型可导出**: 支持导出训练数据和自己的模型
- **OPML 导入**: 支持标准 RSS 订阅导入

## README 中文简介

**RSS Swipr** - 带本地偏好学习的滑动风格 RSS 阅读器

您可以将其作为干净的移动优先体验运行，并在需要时使用完整的桌面端控制。

**快速开始**:

**选项 A: mise + uv (推荐)**:
```bash
git clone https://github.com/philippdubach/rss-swipr.git
cd rss-swipr
mise install
mise run install
mise run dev
```
打开 http://127.0.0.1:5000

**选项 B: 传统 venv**:
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

**核心工作流**:

1. 打开设置（齿轮图标）通过 OPML 导入订阅源
2. 刷新订阅源
3. 滑动或投票卡片以训练您的偏好数据
4. 可选导出训练数据并稍后上传自己的模型

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Tinder 风格 | 滑动卡片交互 | README | 高 |
| 本地学习 | 用户偏好本地训练 | README | 高 |
| 移动优先 | 移动端优化体验 | README | 高 |
| OPML 导入 | 标准 RSS 订阅导入 | README | 高 |
| 模型导出 | 导出训练数据和模型 | README | 高 |
| 投票机制 | 喜欢/不喜欢投票 | README | 高 |
| ML 推荐 | 机器学习推荐 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              RSS Swipr 架构                                  │
│           (Tinder 风格 RSS 阅读器)                         │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              前端层                                │  │
│  │                                                  │  │
│  │   • 卡片式 UI                                    │  │
│  │   • 滑动交互                                     │  │
│  │   • 投票按钮                                     │  │
│  │   • 移动优先设计                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层 (Flask)                        │  │
│  │                                                  │  │
│  │   • RSS 抓取                                     │  │
│  │   • 文章管理                                     │  │
│  │   • 用户交互                                     │  │
│  │   • 设置管理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              ML 层                                 │  │
│  │                                                  │  │
│  │   • 偏好学习                                     │  │
│  │   • 推荐模型                                     │  │
│  │   • 模型导出                                     │  │
│  │   • 训练数据管理                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              数据层                                │  │
│  │                                                  │  │
│  │   • RSS 订阅 (OPML)                              │  │
│  │   • 文章数据                                     │  │
│  │   • 用户偏好                                     │  │
│  │   • 训练数据                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 主应用 | `app.py` | Flask 应用入口 | 核心 |
| 机器学习 | `ml/` | ML 模型和训练 | 核心 |
| 笔记本 | `notebooks/` | Jupyter 笔记本 | 分析 |
| 静态资源 | `static/` | CSS/JS/图片 | 前端 |
| 模板 | `templates/` | HTML 模板 | 前端 |
| 源码 | `src/` | 源代码 | 核心 |
| 热门文章 | `top_articles.py` | 文章分析 | 工具 |

## 运行与开发方式

**推荐方式 (mise + uv)**:
```bash
git clone https://github.com/0smboy/rss-swipr.git
cd rss-swipr
mise install
mise run install
mise run dev
```
访问 http://127.0.0.1:5000

**传统方式**:
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

**开发**:
```bash
# 使用 uv
uv sync
uv run app.py

# 或使用 start.sh
./start.sh
```

## 外部接口

**Web 界面**:
- URL: http://127.0.0.1:5000
- 移动端优化的卡片式界面
- 滑动或点击投票

**OPML 导入**:
- 支持标准 RSS OPML 文件导入
- 设置中上传 OPML 文件

**模型导出**:
- 导出训练数据
- 上传自定义模型

## 数据流 / 控制流

```
RSS 源 (OPML 导入)
    ↓
抓取文章
    ↓
卡片式展示
    ↓
用户滑动/投票
    ↓
偏好学习
    ↓
模型更新
    ↓
推荐排序
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| Flask | Web 框架 | 高 |
| uv | 包管理 | 高 |
| mise | 开发环境 | 中 |
| ML | 推荐系统 | 中 |
| OPML | RSS 标准 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 简洁 | 中 |
| 上手难度 | 低 | mise/uv 一键启动 | 低 |
| 架构复杂度 | 中 | Flask + ML | 中 |
| 外部依赖 | 中 | RSS 源依赖 | 中 |
| Stars | 低 | 4 stars | 低 |
| 维护状态 | 中 | fork 项目 | 中 |

**注意事项**:
- 是 fork 项目（来自 philippdubach/rss-swipr）
- ML 功能需验证实现细节
- RSS 源需要网络连接

**交互方式**:
- 左滑: 不喜欢
- 右滑: 喜欢
- 或点击投票按钮

## 关联概念

- [[RSS]] - Really Simple Syndication
- [[OPML]] - Outline Processor Markup Language
- [[Tinder-UI]] - Tinder 风格界面
- [[ML-Recommendation]] - 机器学习推荐
- [[Flask]] - Python Web 框架
- [[mise]] - 开发环境管理器
- [[uv]] - Python 包管理器

---

> 来源: [GitHub](https://github.com/0smboy/rss-swipr) | 置信度: 基于 GitHub README
> 👤 **作者**: 0smboy (forked from philippdubach/rss-swipr)
> ⭐ **Stars**: 4
> 🔗 **官网**: [GitHub](https://github.com/0smboy/rss-swipr)
> 📜 **许可证**: 未明确
