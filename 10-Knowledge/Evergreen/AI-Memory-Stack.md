---
title: "AI Memory Stack (AI记忆栈)"
type: evergreen
date: 2026-03-31
tags: [evergreen, AI, memory, context, knowledge-management, claude, obsidian]
aliases: [AI-Memory-Stack, 记忆栈, AI上下文管理, 三层记忆架构, Memory-Stack-Compounding]
---

# AI Memory Stack (AI记忆栈)

> **一句话定义**: AI Memory Stack是一套分层上下文管理系统——通过Session Memory (CLAUDE.md)、Knowledge Graph (Obsidian)、Ingestion Pipeline (内容摄入)三层架构，实现AI助手上下文的**复利积累**而非重复消耗。

---

## 核心问题: 会话上下文丢失

### 现实痛点

> "Teams burn 30-40 minutes per Claude session re-explaining what they already knew yesterday. That's a full workday per week lost to repetition."

**本质问题**:
> "Everything is a context problem. When people say AI can't do real work, what they're actually saying is they gave it bad context."

**错误解法**:
- ❌ 更大的上下文窗口
- ❌ 更好的prompt技巧

**正确解法**:
- ✅ 可复利的记忆系统

---

## 三层记忆架构

```
┌─────────────────────────────────────────────────────────────────┐
│                    3-Layer Memory Architecture                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Layer 3: Ingestion Pipeline (摄入层)                          │
│  ───────────────────────────────────                           │
│  视频/播客/文章/会议 → 结构化笔记 → 知识图谱                     │
│                                                                  │
│  关键工具: brain-ingest                                          │
│  ├── 自动转录 (音视频)                                           │
│  ├── 提取关键主张                                                │
│  ├── 识别核心概念                                                │
│  └── 生成Obsidian-ready Markdown                                │
│                              ↓                                   │
│  Layer 2: Knowledge Graph (知识层)                               │
│  ─────────────────────────────────                               │
│  Obsidian Vault + MCP servers                                    │
│  ├── 双向链接: [[note-name]]                                     │
│  ├── 图谱视图: 可视化知识网络                                    │
│  ├── smart-connections: AI发现隐藏关联                           │
│  └── qmd: 快速全文检索                                           │
│                              ↓                                   │
│  Layer 1: Session Memory (会话层)                                │
│  ───────────────────────────────                                 │
│  CLAUDE.md + auto-memory                                         │
│  ├── 项目概述和技术栈                                            │
│  ├── 架构决策和编码规范                                          │
│  └── 跨会话持久化关键决策                                        │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 各层详解

### Layer 1: Session Memory

**CLAUDE.md 作用**:
- 每个新会话自动加载
- 建立基础上下文
- 减少重复解释
- 渐进式积累项目知识

**最小可行版本**:
```markdown
# Project Context

## Overview
[一句话项目描述]

## Tech Stack
- Language:
- Framework:
- Key Dependencies:

## Architecture
[核心架构决策]

## Conventions
- Naming:
- Testing:
- Documentation:

## Common Patterns
[链接到模式文档]
```

### Layer 2: Knowledge Graph

**核心原则**:

> **"Notes named as claims, not categories."**
> （笔记以主张命名，而非分类）

```
❌ 传统分类命名:
   ├── Project-Notes/
   ├── Meeting-Notes/
   └── Research/

✅ 主张命名:
   ├── "Memory systems compound over time"
   ├── "Spec separation reduces LLM uncertainty"
   └── "Error analysis is highest-ROI activity"
```

**为什么重要**:
- 分类命名 → 被动存储
- 主张命名 → 主动思考
- 主张是可验证、可链接的原子知识

**链接即语义**:
> "Links as semantic connections."

```
传统链接系统:
├── 目录结构 = 单一维度层次
└── 标签 = 扁平分类

语义链接系统:
├── 双向链接 = 多维度关联
├── 浮现结构 = 涌现的知识图谱
└── 发现连接 = 产生新洞察
```

### Layer 3: Ingestion Pipeline

**brain-ingest 流程**:
```
输入: 视频/播客/文章/会议录音
  ↓
处理:
├── 转录 (如果是音视频)
├── 提取关键主张
├── 识别核心概念
└── 生成结构化笔记
  ↓
输出: Obsidian-ready Markdown
├── 主张命名
├── 双向链接
├── 标签分类
└── 可执行insight
```

---

## 复利效应: 线性 vs 指数

```
简单重复 vs 复利增长:

简单重复:
├── 每次会话从零开始
├── 重新解释相同背景
├── 30-40分钟/次浪费
└── 线性成本增长

复利增长:
├── 每次会话继承历史
├── 新增知识自动链接
├── 上下文自动丰富
└── 指数价值增长
```

### 时间对比

| 时间 | 线性重复 (旧) | 复利增长 (新) |
|------|--------------|--------------|
| Week 1 | 40min/setup | 40min/setup (基础投入) |
| Week 2 | 40min/setup | 5min/setup (继承历史) |
| Week 3 | 40min/setup | 5min/setup + 新链接 |
| Week 4 | 40min/setup | 5min/setup + 图谱价值 |
| **节省** | **每周1.5天** | **每周0.2天** |

---

## Agent增强图谱

> "Agents improve the graph over time."

**Agent在记忆栈中的角色**:
- 自动提取关键主张
- 建议相关链接
- 发现重复/矛盾
- 推荐归档/更新
- 持续优化结构

---

## 关键数据

| 数字 | 含义 |
|------|------|
| **30-40分钟** | 每次会话重复解释时间 |
| **1天/周** | 线性重复模式下每周浪费的时间 |
| **5分钟** | 复利模式下的新会话准备时间 |
| **3层** | 记忆架构层数 |

---

## 关联概念

- [[Obsidian]] — 知识图谱工具
- [[Claude-Code]] — Session Memory的实践载体
- [[CLAUDE.md]] — 项目级上下文定义
- [[Knowledge-Management]] — 知识管理方法论
- [[Knowledge-Graph]] — 知识图谱技术
- [[Ingestion-Pipeline]] — 内容摄入工作流

---

## 来源引用

- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-18_Claude_Obsidian_Memory_Stack_Compounds_深度解读]] — Claude + Obsidian: 复利增长的记忆栈

---

*创建于 2026-03-18，补充于 2026-03-31，精读深度解读提取*
