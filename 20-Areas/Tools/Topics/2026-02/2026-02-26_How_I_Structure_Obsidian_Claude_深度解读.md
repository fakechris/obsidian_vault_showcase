---
title: How I Structure Obsidian & Claude - 深度解读
author: James Bedford
date: 2026-02-26
type: area-note
tags:
  - obsidian
  - claude
  - workflow
  - productivity
  - context-engineering
  - ai-memory
source: "[[2026-02-26_How_I_Structure_Obsidian_Claude]]"
---

# How I Structure Obsidian & Claude - 深度解读

## 1. 核心洞察 (Insight)

**核心观点**：将 Obsidian 作为思考空间，Claude 文件夹作为执行空间，保持"人机分离"的边界感。

**关键洞见**：
- AI 生成的内容会稀释知识图谱，应当物理隔离
- 人类笔记（思考）与 AI 产出（执行）需要不同的组织结构
- Polaris（北极星）文件夹作为 Claude 的"Top of Mind"上下文锚点

## 2. 架构分析 (Architecture)

### 三层结构
```
Claude Folder/
├── Github/          # 代码库、PRD、技术文档
├── Meeting Notes/   # Granola 导出、会议记录
└── Obsidian Vault/  # 个人写作、思考、日志
```

### Obsidian 五文件夹结构
| 文件夹 | 用途 | Claude 交互方式 |
|--------|------|----------------|
| Polaris | 北极星目标、价值观、Top of Mind | 作为决策参考框架 |
| Logs | 每日笔记（scratchpad） | 回顾、提取行动项 |
| Commonplace | 零散想法、笔记 | 连接、发现隐藏关联 |
| Outputs | 对外发布内容 | 润色、优化 |
| Utilities | 模板、图片、画布 | 辅助工具 |

### 导航系统（三维度）
1. **Folders** - 物理组织，简单可预测
2. **Tags** - 便携、嵌套、Claude 友好
3. **Backlinks** - 手动连接，发现隐藏关联

## 3. 关键方法论 (Methodology)

### Life Razor（生命剃刀）
- 用一句话定义人生使命
- 作为所有决策的过滤器
- Prompt: "How does this help or detract from my life razor?"

### Idea Report Prompt
```
"I have a few hours of spare focus time - what should I work on?"
```
Claude 基于全部上下文给出跨领域建议。

### Top of Mind 机制
- 每两周更新一次
- 包含当前优先级、目标、价值观
- Claude 频繁引用以保持聚焦

## 4. 实践应用 (Application)

### 会议准备 Workflow
```
"I have a 121 upcoming with X person, what were the actions
we took in our last meeting, and is there anything I need
to do prior to our call?"
```

### PRD → Linear 自动化
```
"Look at the latest PRD and create me a Linear project
from the PRD. Create specific tasks for each stage."
```

### 决策对齐检查
```
"How are my current actions aligned with what's top of my mind?"
```

## 5. 关联网络 (Connections)

**向上链接**：
- [[40-Resources/Evergreen/Context-Engineering]] - 上下文工程原则
- [[20-Areas/AI-Research/Personal-Brain-OS]] - 文件系统作为数据库的理念

**同级链接**：
- [[Claude-Cowork-非开发者指南]] - 非开发者使用模式
- [[Claude-Code-三阶段工作流]] - 编码场景的工作流

**向下链接**：
- 具体 Prompt 模板
- 个人 vault 结构调整指南

## 6. 批判性思考 (Critique)

### 优点
- 分离关注点的架构清晰
- Polaris 作为"北极星"的隐喻直观有效
- Tag 系统的可移植性强

### 局限
- 需要维护两套系统的同步
- "Life Razor" 可能过于简化复杂的人生决策
- 对非英语用户的 Voice 适配未提及

### 适配建议
- 中文用户可增加 "主题分类" 维度
- 考虑添加 "回顾周期"（每周/每月）的自动化

## 质量评估

| 维度 | 评分 | 说明 |
|------|------|------|
| 原创性 | 7/10 | 整合 PARA + Zettelkasten + AI 工作流 |
| 实用性 | 9/10 | 可直接复制的工作流结构 |
| 深度 | 7/10 | 方法论清晰但理论支撑较少 |
| 可操作性 | 9/10 | 具体文件夹结构和 Prompt 示例 |
| 可扩展性 | 8/10 | 框架灵活，易于个性化调整 |
| 时效性 | 8/10 | 基于当前 Claude-Obsidian 集成能力 |

**总分**：48/60（高质量实践指南）
