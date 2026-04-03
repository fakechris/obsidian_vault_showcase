---
title: Home
type: meta
date: 2026-03-30
tags: [meta, navigation]
aliases: [首页, Dashboard, 主页]
---

# 🏠 OpenClaw Vault

> 个人知识库 — 由人工 + AI Bot 协同维护

---

## 🧭 三层架构导航

### Layer 1: Session Memory (会话层)
| 目录 | 说明 | 入口 |
|------|------|------|
| 🧭 [[00-Polaris/README\|00-Polaris]] | 指南针层 — 当前焦点、Life Razor、项目状态 | [[00-Polaris/Top-of-Mind\|Top of Mind]] |
| 📝 [[60-Logs/README\|60-Logs]] | 日志层 — 每日笔记、周回顾、会话记录 | [[60-Logs/Weekly/\|周回顾]] |

### Layer 2: Knowledge Graph (知识层)
| 目录 | 说明 | 入口 |
|------|------|------|
| 📚 [[10-Knowledge/README\|10-Knowledge]] | 知识层 — 常青笔记、概念图谱 | [[10-Knowledge/Atlas/MOC-Index\|Atlas]] |
| 🎯 [[20-Areas/README\|20-Areas]] | 领域层 — 持续维护的责任领域 | [[20-Areas/AI-Research/MOC\|AI 研究]] |
| 🚀 [[30-Projects/README\|30-Projects]] | 项目层 — 有截止时间的承诺 | [[30-Projects/Active/\|活跃项目]] |
| 📦 [[40-Resources/README\|40-Resources]] | 资源层 — 模板、代码片段 | [[40-Resources/Templates/\|模板]] |

### Layer 3: Ingestion (摄入层)
| 目录 | 说明 | 入口 |
|------|------|------|
| 📥 [[50-Inbox/README\|50-Inbox]] | 收集箱 — 三层捕获系统 | [[50-Inbox/01-Raw/\|原始文章]] |

### Archive
| 目录 | 说明 |
|------|------|
| 📦 [[70-Archive/README\|70-Archive]] | 归档层 — 已完成的内容 |

---

## 🔥 当前焦点

从 [[00-Polaris/Top-of-Mind\|Top of Mind]]:
1. **OpenClaw Vault 三层架构重构** — 进行中 🟡
2. **AI 投资研究体系** — 活跃 🟢
3. **Claude Code 工作流优化** — 活跃 🟢

---

## 📊 Vault 统计

```dataview
TABLE length(rows) AS "笔记数"
FROM ""
WHERE type != null AND type != "meta"
GROUP BY type
SORT length(rows) DESC
```

---

## 🕐 最近更新

```dataview
TABLE title, type, date, file.folder
FROM ""
WHERE type != null AND type != "meta"
SORT file.mtime DESC
LIMIT 10
```

---

## 🛠 快捷操作

### 创建新内容
- 新建文章解读: 使用 `40-Resources/Templates/文章解读`
- 新建项目笔记: 使用 `40-Resources/Templates/项目笔记`
- 新建常青笔记: 使用 `10-Knowledge/Evergreen/_template`

### 维护任务
- [[00-Polaris/Weekly-Review\|周回顾]] — 使用周回顾模板
- [[50-Inbox/README\|整理 Inbox]] — 处理收集箱

---

## 🔗 外部链接

- [[Tags\|标签体系]] — 完整的标签分类
- [[README\|项目 README]] — Vault 说明文档
- [[BOT_GUIDE\|Bot 协同指南]] — AI Bot 工作流程

---

> [!tip] 提示
> 这是 Vault 的入口页面。使用左侧目录或上方导航链接探索知识库。
> Claude 会在每次会话开始时读取 [[00-Polaris/Top-of-Mind\|Top of Mind]] 了解你的当前上下文。
