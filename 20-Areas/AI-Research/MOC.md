---
title: "AI-Research MOC"
type: moc
date: 2026-03-31
tags: [moc, areas, ai, research]
aliases: [AI研究, AI Research]
---

# 🤖 AI-Research MOC

> AI 行业研究 — 追踪技术趋势、论文、产品
>
> **常青笔记**: [[../../10-Knowledge/Atlas/MOC-Index\|63个核心概念]] | **深度解读**: [[Topics/AI MOC\|196+篇研究]]

---

## 📊 研究概览

```dataview
TABLE title, date, tags
FROM "20-Areas/AI-Research"
WHERE type = "analysis" OR type = "raw-article"
SORT date DESC
LIMIT 10
```

---

## 📁 子目录

| 目录 | 内容 | 入口 |
|------|------|------|
| Papers/ | 论文笔记、研究解读 | [[Papers/Papers MOC\|Papers MOC]] |
| Topics/ | 主题研究 | [[Topics/AI MOC\|Topics MOC]] |

---

## 🌐 常青笔记索引 (63个)

### Agent 核心架构
- [[../../10-Knowledge/Evergreen/AI-Agent\|AI-Agent]] — Agent基础概念
- [[../../10-Knowledge/Evergreen/Agent-Architecture\|Agent-Architecture]] — Agent架构设计
- [[../../10-Knowledge/Evergreen/Agent-Harness\|Agent-Harness]] — Agent训练环境
- [[../../10-Knowledge/Evergreen/Agent-Orchestrator\|Agent-Orchestrator]] — Agent编排系统
- [[../../10-Knowledge/Evergreen/Multi-Agent-Orchestration-Patterns\|Multi-Agent-Orchestration-Patterns]] — 多Agent编排模式
- [[../../10-Knowledge/Evergreen/Agent-Evaluation\|Agent-Evaluation]] — Agent评估方法论
- [[../../10-Knowledge/Evergreen/Multi-Agent-Collaboration\|Multi-Agent-Collaboration]] — 多Agent协作
- [[../../10-Knowledge/Evergreen/Constrained-Autonomy\|Constrained-Autonomy]] — 约束自主性设计
- [[../../10-Knowledge/Evergreen/Claude-Code-Agent-Teams\|Claude-Code-Agent-Teams]] — Claude Code Agent Teams
- [[../../10-Knowledge/Evergreen/Hyperagents\|Hyperagents]] — 元认知自修改Agent
- [[../../10-Knowledge/Evergreen/Machine-Builds-Machine\|Machine-Builds-Machine]] — AI管理工程

### 记忆与上下文系统
- [[../../10-Knowledge/Evergreen/Agent-Memory\|Agent-Memory]] — Agent记忆系统
- [[../../10-Knowledge/Evergreen/Memory-Systems-Architecture\|Memory-Systems-Architecture]] — 记忆系统架构
- [[../../10-Knowledge/Evergreen/Work-Memory-as-Moat\|Work-Memory-as-Moat]] — 工作记忆护城河
- [[../../10-Knowledge/Evergreen/Dynamic-Context-Discovery\|Dynamic-Context-Discovery]] — 动态Context发现
- [[../../10-Knowledge/Evergreen/Context-Engineering\|Context-Engineering]] — 上下文工程
- [[../../10-Knowledge/Evergreen/Context-Compaction\|Context-Compaction]] — 上下文压缩
- [[../../10-Knowledge/Evergreen/Prompt-Caching\|Prompt-Caching]] — Prompt缓存技术
- [[../../10-Knowledge/Evergreen/Prompt-Caching-Token-Economics\|Prompt-Caching-Token-Economics]] — Prompt缓存代币经济学
- [[../../10-Knowledge/Evergreen/Backpressure\|Backpressure]] — 反压机制设计
- [[../../10-Knowledge/Evergreen/Reflexion-System\|Reflexion-System]] — 反思系统

### Skills 与工具系统
- [[../../10-Knowledge/Evergreen/Skills\|Skills]] — Agent技能系统
- [[../../10-Knowledge/Evergreen/Claude-Skills-Taxonomy\|Claude-Skills-Taxonomy]] — Skills分类体系
- [[../../10-Knowledge/Evergreen/Agent-Tools-Design\|Agent-Tools-Design]] — Agent工具设计
- [[../../10-Knowledge/Evergreen/ADK-Skill-Design-Patterns\|ADK-Skill-Design-Patterns]] — ADK Skill设计模式
- [[../../10-Knowledge/Evergreen/MCP\|MCP]] — Model Context Protocol
- [[../../10-Knowledge/Evergreen/Spec-Driven-Development\|Spec-Driven-Development]] — Spec驱动开发
- [[../../10-Knowledge/Evergreen/CLAUDE-md-Engineering\|CLAUDE-md-Engineering]] — CLAUDE.md工程方法论
- [[../../10-Knowledge/Evergreen/gstack\|gstack]] — 专家思维模式编码
- [[../../10-Knowledge/Evergreen/Trading-as-Git\|Trading-as-Git]] — 交易版本控制范式

### 评估与验证系统
- [[../../10-Knowledge/Evergreen/Deep-Agents-Evals\|Deep-Agents-Evals]] — Deep Agents评估
- [[../../10-Knowledge/Evergreen/Evaluation-Flywheel\|Evaluation-Flywheel]] — 评估飞轮
- [[../../10-Knowledge/Evergreen/Resolution-Rate\|Resolution-Rate]] — 业务导向评估指标
- [[../../10-Knowledge/Evergreen/Verification-Economy\|Verification-Economy]] — 验证经济
- [[../../10-Knowledge/Evergreen/Adversarial-Review\|Adversarial-Review]] — 对抗性审查
- [[../../10-Knowledge/Evergreen/Sandbox\|Sandbox]] — 沙箱安全机制
- [[../../10-Knowledge/Evergreen/Claude-Code-Auto-Mode\|Claude-Code-Auto-Mode]] — Claude Code Auto Mode
- [[../../10-Knowledge/Evergreen/Type-First-Function-Calling-Harness\|Type-First-Function-Calling-Harness]] — 类型优先Function Calling

### Harness 工程与RL
- [[../../10-Knowledge/Evergreen/Harness-Engineering\|Harness-Engineering]] — Harness工程
- [[../../10-Knowledge/Evergreen/Agentic-RL\|Agentic-RL]] — Agentic强化学习
- [[../../10-Knowledge/Evergreen/Multi-Agent-Simulation-for-Prediction\|Multi-Agent-Simulation-for-Prediction]] — 多智能体模拟预测
- [[../../10-Knowledge/Evergreen/Why-How-Loop-Framework\|Why-How-Loop-Framework]] — Why-How Loop人机协作框架
- [[../../10-Knowledge/Evergreen/Reference-Application-Anchoring\|Reference-Application-Anchoring]] — 参考应用锚定
- [[../../10-Knowledge/Evergreen/Step-Level-Durable-Execution\|Step-Level-Durable-Execution]] — 步骤级持久执行
- [[../../10-Knowledge/Evergreen/Long-Running-Agent-Harness\|Long-Running-Agent-Harness]] — 长运行Agent Harness

### 新兴范式与协议
- [[../../10-Knowledge/Evergreen/Deep-Agents\|Deep-Agents]] — 深度Agent概念
- [[../../10-Knowledge/Evergreen/Intention-Layer\|Intention-Layer]] — 意图层协议
- [[../../10-Knowledge/Evergreen/Prediction-Market\|Prediction-Market]] — 预测市场
- [[../../10-Knowledge/Evergreen/Knowledge-Overhang-in-LLMs\|Knowledge-Overhang-in-LLMs]] — LLM知识悬垂现象
- [[../../10-Knowledge/Evergreen/Organization-as-Intelligence\|Organization-as-Intelligence]] — 组织即智能
- [[../../10-Knowledge/Evergreen/Autopilot-Business-Model\|Autopilot-Business-Model]] — Autopilot商业模式
- [[../../10-Knowledge/Evergreen/Polymarket-Arbitrage-Math\|Polymarket-Arbitrage-Math]] — Polymarket套利数学
- [[../../10-Knowledge/Evergreen/AI-SaaS-Disruption\|AI-SaaS-Disruption]] — AI SaaS颠覆
- [[../../10-Knowledge/Evergreen/Prompt-Injection\|Prompt-Injection]] — Prompt注入攻击

---

## 📈 追踪清单

- [ ] 每周阅读 5 篇 AI 文章
- [ ] 每月完成 1 篇深度分析
- [ ] 每季度更新 AI 趋势判断

---

## 🔗 相关

- [[../../10-Knowledge/Atlas/MOC-Index\|Atlas 知识地图]] — 所有常青笔记索引
- [[Topics/AI MOC\|AI Topics MOC]] — AI主题详细索引
- [[20-Areas/README\|返回 Areas 层]]
- [[../../Home\|Vault 首页]]

---

> [!tip] 快速导航
> 使用 `[[` 触发链接补全，或查看 [[../../10-Knowledge/Atlas/MOC-Index\|Atlas 知识地图]] 获取完整概念图谱。
