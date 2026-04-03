---
title: "Obsidian Vault Showcase"
description: "带完整Demo的开箱即用知识库"
date: 2026-04-03
type: meta
---

# Obsidian Vault Showcase

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Obsidian](https://img.shields.io/badge/Obsidian-Plugin-7C3AED?logo=obsidian)](https://obsidian.md)

**带完整Demo的开箱即用Obsidian知识库**

🌳 8个Evergreen概念 • 📚 76篇深度解读 • 🗺️ 3个知识地图

[📖 浏览内容](#浏览内容) • [🚀 快速开始](#快速开始) • [⬇️ 下载使用](#下载使用)

</div>

---

## 两个项目，两种选择

| 项目 | 定位 | 适合场景 |
|------|------|----------|
| **obsidian_vault_showcase** | **带Demo的开箱即用版本（本项目）** | 想先看效果，或基于现有内容继续 |
| [**obsidian_vault_pipeline**](https://github.com/fakechris/obsidian_vault_pipeline) | **纯代码模板** | 想从零开始，理解Pipeline实现 |

### 如何选择？

| 你的需求 | 推荐项目 | 原因 |
|----------|----------|------|
| 想先看看效果再决定是否使用 | **本项目** | 有76篇真实内容可浏览 |
| 想开箱即用，在上面改 | **本项目** | 克隆后直接Obsidian打开 |
| 想从零开始，完全自定义 | [obsidian_vault_pipeline](https://github.com/fakechris/obsidian_vault_pipeline) | 空白模板，无demo数据 |
| 想了解Pipeline技术实现 | [obsidian_vault_pipeline](https://github.com/fakechris/obsidian_vault_pipeline) | 代码结构更清晰 |
| 想基于现有内容继续生成 | **本项目** | 已有内容+完整脚本 |

---

## 浏览内容

### 直接在GitHub上浏览

| 目录 | 内容 |
|------|------|
| [10-Knowledge/Evergreen/](10-Knowledge/Evergreen/) | 8个原子概念笔记 |
| [10-Knowledge/Atlas/](10-Knowledge/Atlas/) | 3个MOC知识地图 |
| [20-Areas/Tools/](20-Areas/Tools/) | 70个GitHub项目分析 |
| [20-Areas/Programming/](20-Areas/Programming/) | 编程技术深度解读 |
| [20-Areas/AI-Research/](20-Areas/AI-Research/) | AI研究文章解读 |

### 内容示例

**Evergreen 笔记**:
- [Agent Harness](10-Knowledge/Evergreen/Agent-Harness.md) - 完整的agent环境设计框架
- [Prompt Caching](10-Knowledge/Evergreen/Prompt-Caching.md) - 长会话优化核心技术
- [Context Engineering](10-Knowledge/Evergreen/Context-Engineering.md) - 上下文管理

**深度解读**:
- [Kaku - AI编程终端](20-Areas/Tools/Topics/2026-02/2026-04-02_tw93_kaku.md)
- [Levelsio Claude Code 10x实践](20-Areas/Programming/Levelsio-Claude-Code-10x实践.md)
- [Claude Prompt Auto-Caching](20-Areas/Programming/Claude-Prompt-Auto-Caching.md)

---

## 快速开始

### 方式一：只看效果（推荐新手）

直接在GitHub上浏览上述链接，查看内容结构和质量。

### 方式二：本地体验Obsidian

```bash
# 克隆项目
git clone https://github.com/fakechris/obsidian_vault_showcase.git my-vault
cd my-vault

# 用Obsidian打开
# 1. 打开Obsidian应用
# 2. "Open folder as vault"
# 3. 选择 my-vault 目录
# 4. 查看Graph View体验双向链接网络
```

### 方式三：在此基础上继续生成（开发者）

本项目包含完整的Pipeline脚本，配置API Key后可继续生成内容：

```bash
# 1. 配置API Key（交互式向导）
python3 60-Logs/scripts/unified_pipeline_enhanced.py --init

# 2. 验证环境
python3 60-Logs/scripts/unified_pipeline_enhanced.py --check

# 3. 安装依赖
pip install -r requirements.txt

# 4. 运行Pipeline继续生成
python3 60-Logs/scripts/unified_pipeline_enhanced.py --full
```

---

## 下载使用

### 环境要求

- **Obsidian**: 最新版本（用于浏览和编辑）
- **Python**: 3.10+（用于运行Pipeline生成新内容）
- **API Key**: MiniMax/Anthropic/OpenAI（可选，用于生成）

### 文件说明

```
my-vault/
├── 00-Polaris/Home.md          # Obsidian首页入口
├── 10-Knowledge/
│   ├── Evergreen/              # 8个原子概念笔记
│   └── Atlas/                  # 3个MOC知识地图
├── 20-Areas/                   # 76篇深度解读
├── 50-Inbox/                   # 待处理内容（空，等你填充）
├── 60-Logs/
│   └── scripts/                # ✅ 完整Pipeline脚本
│       ├── unified_pipeline_enhanced.py  # 主入口
│       ├── auto_article_processor.py
│       ├── auto_evergreen_extractor.py
│       └── ...
├── 90-Templates/               # 笔记模板
└── requirements.txt            # Python依赖
```

### 配置API Key

编辑 `.env` 文件（从 `.env.example` 复制）：

```bash
# LLM API（必需，用于生成新内容）
AUTO_VAULT_API_KEY=your_key_here
AUTO_VAULT_API_BASE=https://api.minimaxi.com/anthropic
AUTO_VAULT_MODEL=minimax/MiniMax-M2.5

# Pinboard（可选，用于自动抓取书签）
PINBOARD_TOKEN=username:token
```

---

## 核心特性

本项目展示了以下Pipeline能力：

- ✅ **6维度深度解读** - 定义/解释/细节/架构/行动/关联
- ✅ **Evergreen原子笔记自动提取** - LLM识别核心概念
- ✅ **MOC知识地图自动维护** - 双向链接导航
- ✅ **质量门禁系统** - 提交前自动检查
- ✅ **WIGS完整性保障** - 5层一致性检查
- ✅ **结构化审计日志** - JSONL格式完整追踪

---

## 从Showcase到生产

如果你想清空demo数据，建立自己的系统：

```bash
# 1. Fork或克隆本项目
git clone https://github.com/fakechris/obsidian_vault_showcase.git my-vault
cd my-vault

# 2. 删除demo数据（保留目录结构和脚本）
rm -rf 10-Knowledge/Evergreen/*.md
rm -rf 20-Areas/*/*/*.md
rm -rf 10-Knowledge/Atlas/*.md

# 3. 配置API Key
python3 60-Logs/scripts/unified_pipeline_enhanced.py --init

# 4. 运行Pipeline，生成你自己的内容
python3 60-Logs/scripts/unified_pipeline_enhanced.py --full
```

或者，直接使用[obsidian_vault_pipeline](https://github.com/fakechris/obsidian_vault_pipeline)模板项目（已经为空）。

---

## 内容来源与质量

本showcase中的内容均为公开技术文章、GitHub项目文档和学术论文的深度解读，用于展示知识管理系统的结构和质量。

**6维度质量模型**:
1. 一句话定义
2. 详细解释 (What/Why/How)
3. 重要细节 (≥3 个技术点)
4. 架构图/流程图
5. 行动建议 (≥2 条)
6. 关联知识 (双向链接)

---

## 许可证

MIT License - 详见 [LICENSE](LICENSE)

---

*版本: 1.0 | 基于 [obsidian_vault_pipeline](https://github.com/fakechris/obsidian_vault_pipeline) | 95 个文件 | 约 25,000 行内容*
