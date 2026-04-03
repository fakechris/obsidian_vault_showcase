---
title: "James Bedford Obsidian+Claude工作流 - 分离式知识管理"
author: James Bedford (@jameesy)
source: https://x.com/jameesy/status/2026628809424781787
date: 2026-02-26
type: evergreen-note
tags: [Obsidian, Claude, Workflow, Knowledge-Management, Productivity]
---

# James Bedford Obsidian+Claude工作流 - 分离式知识管理

> **一句话定义**: 一套将AI生成内容与人类写作分离的Obsidian+Claude工作流，通过专用Claude文件夹隔离生成内容，保持Obsidian知识图谱纯净，同时充分利用Claude的上下文理解能力。

---

## 详细解释

### What
James Bedford的Obsidian+Claude整合方案：
- **分离原则**: AI生成内容与人类写作物理隔离
- **专用Claude文件夹**: 包含Github代码库、会议笔记转录、Claude配置文件
- **5文件夹Obsidian结构**: Polaris(北极星目标)、Logs(日志)、Commonplace(笔记)、Outputs(输出)、Utilities(工具)
- **三层导航**: 文件夹 + 标签 + 反向链接
- **核心工具**: "Top of Mind"指导文档、Life Razor人生剃刀、Idea Report创意报告

### Why
**避免的问题**:
- 知识图谱被大量转录/生成文件稀释
- AI生成内容视觉上干扰人类写作
- 上下文过载导致Claude效率下降

**分离的好处**:
- Obsidian保持为"人类思考空间"
- Claude仍可访问所有上下文（通过专用文件夹）
- 知识图谱保持有意义的人类连接
- 6年Obsidian使用经验验证的简单结构

### How
**目录结构**:
```
~/claude/                    # 专用Claude文件夹
├── Github/                  # 代码库
│   ├── personal-codebases/  # 个人项目
│   ├── work-codebases/      # 工作项目
│   └── Zkills/              # 公司skills/docs知识库
├── Meeting Notes/           # Granola会议笔记导出
└── ...

~/Obsidian Vault/            # Obsidian主库
├── Polaris/                 # 北极星：目标、抱负、Top of Mind
├── Logs/                    # 每日笔记（scratchpad）
├── Commonplace/             # 主要笔记空间（commonplace book）
├── Outputs/                 # 待分享写作
└── Utilities/               # 图片、模板、canvas、人物
```

**关键Prompts**:
- "Look at the latest PRD and create me a Linear project from the PRD. Create specific tasks for each stage"
- "I have a 121 upcoming with X person, what were the actions we took in our last meeting?"
- "How are my current actions aligned with what's top of my mind?"
- "I am thinking about taking on X opportunity.. How does this help or detract from my life razor?"
- "I have a few hours of spare focus time - what should I work on?" (Idea Report)

---

## 3个重要细节

### 1. Polaris文件夹 - 方向指引系统
Polaris文件夹的核心是"Top of Mind"文档：
- 每几周更新一次
- 记录当前最重要的事项和目标
- 作为Claude的参考点，使其思考保持聚焦
- 防止追逐"闪亮的新事物"

**Life Razor概念**: 用一句话定义人生使命。例: "How does this help or detract from my life razor?"

### 2. Tags的充分利用
James强调Tags是Obsidian中最被低估的导航方式：
- **可嵌套**: `#project/client-a` 层级结构
- **文件优先**: 保持"file over app"理念，标签随文件移动
- **Claude友好**: "look for notes within the #articles tag"
- **跨文件夹**: 无视物理位置组织内容

### 3. Idea Report - 创意发现Prompt
最喜爱的Prompt: "I have a few hours of spare focus time - what should I work on?"

Claude输出结构：
- 不同领域的建议
- 可以构建的东西
- 需要联系的人
- 需要调查或基于其构建的想法
- 可能遗漏的行动项
- 跨引用思考，展示想法间的连接

---

## 架构图

```
┌────────────────────────────────────────────────────────────────────────┐
│                 James Bedford Obsidian + Claude Setup                 │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │                        CLAUDE FOLDER                              │  │
│  │  (所有AI生成内容、转录、代码库、配置文件)                         │  │
│  │                                                                   │  │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │  │
│  │  │  Github/    │  │Meeting      │  │  Claude Configs/        │  │  │
│  │  │  • 个人代码  │  │Notes/       │  │  • Skills              │  │  │
│  │  │  • 工作代码  │  │• Granola    │  │  • 仓库配置            │  │  │
│  │  │  • Zkills   │  │  导出       │  │  • MCP设置             │  │  │
│  │  └─────────────┘  └─────────────┘  └─────────────────────────┘  │  │
│  │                                                                   │  │
│  │  ✓ Claude有完全上下文访问权限                                    │  │
│  │  ✓ 不污染Obsidian知识图谱                                        │  │
│  │  ✓ 可用于自动化任务（PRD→Linear项目）                            │  │
│  └──────────────────────────────────────────────────────────────────┘  │
│                                                                        │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │                      OBSIDIAN VAULT                              │  │
│  │              (人类写作和思考空间 - 保持纯净)                       │  │
│  │                                                                   │  │
│  │  ┌──────────┐ ┌──────────┐ ┌────────────┐ ┌──────────┐         │  │
│  │  │ Polaris/ │ │ Logs/    │ │Commonplace/│ │Outputs/  │         │  │
│  │  │ 北极星    │ │ 每日笔记 │ │  主笔记空间 │ │ 分享写作 │         │  │
│  │  │          │ │          │ │            │ │          │         │  │
│  │  │ • Top of │ │ • Scratch│ │ • 各主题   │ │ • 文章   │         │  │
│  │  │   Mind   │ │   pad    │ │   笔记     │ │ • 社交   │         │  │
│  │  │ • 目标   │ │ • 每日   │ │ • 思考连接 │ │   媒体   │         │  │
│  │  │ • Life   │ │   记录   │ │ • 个人知识 │ │          │         │  │
│  │  │   Razor  │ │          │ │   库       │ │          │         │  │
│  │  └──────────┘ └──────────┘ └────────────┘ └──────────┘         │  │
│  │                                                                   │  │
│  │  导航方式：Folders + Tags + Backlinks                            │  │
│  │  Tags示例：#project/client-a, #articles, #ideas                   │  │
│  └──────────────────────────────────────────────────────────────────┘  │
│                                                                        │
│  ┌──────────────────────────────────────────────────────────────────┐  │
│  │                      KEY PROMPTS                                   │  │
│  │                                                                   │  │
│  │  方向对齐    → "How are my current actions aligned with             │  │
│  │              what's top of my mind?"                              │  │
│  │                                                                   │  │
│  │  决策评估    → "How does X help or detract from my                │  │
│  │              life razor?"                                         │  │
│  │                                                                   │  │
│  │  会议准备    → "I have a 121 with X, what were the actions        │  │
│  │              from our last meeting?"                              │  │
│  │                                                                   │  │
│  │  创意发现    → "I have a few hours - what should I work on?"      │  │
│  │              (Idea Report)                                        │  │
│  │                                                                   │  │
│  │  项目创建    → "Look at the latest PRD and create a Linear        │  │
│  │              project with specific tasks"                         │  │
│  └──────────────────────────────────────────────────────────────────┘  │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 2条行动建议

### 建议1: 实施分离式内容管理
- 创建专用Claude文件夹，与Obsidian vault物理分离
- 将AI生成内容（转录、PRD、自动输出）放入Claude文件夹
- 保持Obsidian为人类写作和思考的纯净空间
- 确保Claude可通过MCP或路径配置访问两个位置

### 建议2: 建立方向指引系统
- 创建"Top of Mind"文档，记录当前最重要的2-3个优先事项
- 定义个人"Life Razor"（一句话人生使命）
- 定期（每2-4周）更新Polaris内容
- 在关键决策prompts中引用这些方向文档，保持AI建议的聚焦性

---

## 关联知识链接

- [[Obsidian Workflow]] - Obsidian工作流
- [[Claude Code Integration]] - Claude Code集成
- [[PARA Method]] - PARA组织法
- [[Commonplace Book]] - Commonplace笔记法
- [[Knowledge Graph]] - 知识图谱
- [[AI-Human Collaboration]] - AI-人类协作
- [[Life Razor]] - 人生剃刀概念

---

## 参考原文

- 原文文件: [[../../50-Inbox/03-Processed/2026-02-26_How_I_Structure_Obsidian_Claude|原文存档]]
- X/Twitter: https://x.com/jameesy/status/2026628809424781787

---

*创建于: 2026-03-30 | 处理批次: 第一批-08*
