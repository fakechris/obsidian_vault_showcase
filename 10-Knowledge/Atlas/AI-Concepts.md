---
title: "AI Concepts MOC"
type: moc
date: 2026-03-30
tags: [atlas, moc, ai, concepts]
aliases: [AI概念, AI Concepts]
---

# 🤖 AI Concepts MOC

> AI 核心概念图谱 — 从 Agent 到向量存储

---

## 🎯 核心概念

### Agent 架构
- [[Evergreen/AI-Agent\|AI Agent]] — 什么是 AI Agent？
- [[Evergreen/Agent-Orchestrator\|Agent Orchestrator]] — 多 Agent 协作
  - [[OpenClaw-Agent-Swarm\|OpenClaw Agent Swarm]] — Elvis Sun的一人开发团队实现
  - [[../../20-Areas/AI-Research/Topics/Karpathy-Multi-Agent-Research\|Karpathy多代理研究实验]] — 研究组织即代码
  - [[AgentCompany-Overview\|AgentCompany]] — 桌面AI公司
  - [[../../20-Areas/AI-Research/Topics/Build-vs-Buy-Coding-Agents\|Build vs Buy]] — 规模化部署决策
  - [[../../20-Areas/AI-Research/2026-02-24_OpenClaw_Agent_Swarm_深度解读\|OpenClaw Agent Swarm深度解读]] — 完整8步工作流系统
  - [[../../20-Areas/AI-Research/2026-02-24_Self_Improving_AI_System_深度解读\|Agent Orchestrator]] — 自改进8插件槽架构
  - [[Evergreen/Symphony-Experiment\|Symphony Experiment]] — OpenAI Symphony 36小时实验
- [[Evergreen/Agent-Harness\|Agent Harness]] — Agent 框架与治理（已更新Harness > Model洞察）
  - [[../../20-Areas/AI-Research/Topics/Harness-Engineering-Is-Cybernetics\|Harness即控制论]] — 控制论视角
  - [[../../20-Areas/AI-Research/Topics/Harness-Engineering-Same-Old-Story\|Harness Engineering老故事]] — 批判性视角
  - [[../../20-Areas/AI-Research/Topics/Anatomy-of-Agent-Harness\|Harness的解剖]] — 组件详解
  - [[30-Projects/Active/OpenAI-Symphony/Machine-Builds-Machine\|构建机器的机器]] — Symphony案例
  - [[Evergreen/Minimal-Harness\|Minimal Harness]] — 极简Harness批判视角
- [[Evergreen/Agent-Memory\|Agent Memory]] — Agent 记忆系统（已添加QMD实践案例）
  - [[2026-03-01_Claude_Code_Remember_Things_深度解读_v2\|Claude Code记忆系统]] — QMD+语义搜索
  - [[2026-03-01_Grep_Is_Dead_Claude_Code_Memory_深度解读_v2\|Grep is Dead]] — 英文版
  - [[2026-03-01_Grep已死_Claude-Code记忆系统_深度解读_v2\|Grep已死]] — 中文版
- [[Evergreen/Financial-Research-Agent\|Financial Research Agent]] — 金融研究Agent（Dexter案例）
  - [[20-Areas/Investing/Topics/2026-02/2026-02-23_Dexter_Financial_Agent_深度解读\|Dexter深度解读]] — 自主金融研究Agent实现
- [[Evergreen/Content-Ingestion-Skill\|Content Ingestion Skill]] — 内容摄取Skill（DeepReader案例）
  - [[../../20-Areas/AI-Research/2026-02-23_OpenClaw_DeepReader_深度解读\|DeepReader深度解读]] — URL到Markdown自动转换
- [[Evergreen/Context-Engineering\|Context Engineering]] — 上下文工程
  - [[../../20-Areas/AI-Research/Topics/Codex-Context-Compaction\|Codex上下文压缩机制]] — 逆向工程分析
- [[Evergreen/Progressive-Disclosure\|Progressive Disclosure]] — 渐进式披露（已完善三层漏斗模型）
- [[Evergreen/Agentic-Engineering\|Agentic Engineering]] — 与AI协作的方法论
  - [[../../20-Areas/AI-Research/Topics/Writing-Code-Is-Cheap-Now\|Writing code is cheap now]] — Simon Willison的Agentic Engineering核心原则
  - [[2026-03-01_Agent_Harness_Real_Product_深度解读_v2\|Agent Harness is the Real Product]] — Harness > Model
  - [[2026-03-01_Agent_Harness_Real_Product_深度解读_v2\|Agent Harness is the Real Product]] — Harness > Model
  - [[2026-03-01_Agent_Harness_is_the_Real_Product_深度解读_v2\|Agent Harness深度对比]] — 各公司Harness架构
  - [[2026-03-01_First_Run_The_Tests_Agentic_Engineering_深度解读_v2\|First Run The Tests]] — 测试模式
  - [[2026-03-01_Hoard_Things_You_Know_Agentic_Engineering_深度解读_v2\|Hoard Things You Know]] — 知识囤积
  - [[2026-03-01_Interactive_Explanations_Agentic_Engineering_深度解读_v2\|Interactive Explanations]] — 交互式解释
  - [[Evergreen/Agentic-Coding\|Agentic Coding]] — 智能体编程范式转变与批判

### Claude 生态
- [[Evergreen/Claude-Code\|Claude Code]] — Claude Code 核心概念
- [[Evergreen/Claude-API\|Claude API]] — API 使用与限制
- [[Evergreen/Prompt-Caching\|Prompt Caching]] — 提示缓存机制
  - [[Evergreen/ToolSearch-Lazy-Loading\|ToolSearch Lazy Loading]] — 延迟加载非核心工具保护Prompt Cache

### 协议与标准
- [[Evergreen/MCP-Protocol\|MCP Protocol]] — Model Context Protocol
- [[Evergreen/Function-Calling\|Function Calling]] — 工具调用
- [[Evergreen/Structured-Output\|Structured Output]] — 结构化输出

---

## 🧠 技术概念

### 模型
- [[Evergreen/LLM-Architecture\|LLM Architecture]] — 大模型架构
- [[Evergreen/Transformer\|Transformer]] — Transformer 原理
- [[Evergreen/Attention-Mechanism\|Attention Mechanism]] — 注意力机制
- [[Evergreen/Paged-Attention\|Paged Attention]] — vLLM 优化

### 向量与检索
- [[Evergreen/Vector-Store\|Vector Store]] — 向量存储
- [[Evergreen/RAG\|RAG]] — Retrieval-Augmented Generation
- [[Evergreen/Embedding\|Embedding]] — 嵌入向量

---

## 🔄 开发概念

### 工作流
- [[Evergreen/Vibe-Coding\|Vibe Coding]] — AI 驱动开发
- [[Evergreen/Skill-System\|Skill System]] — Claude Skills
- [[Evergreen/Context-Engineering\|Context Engineering]] — 上下文工程
- [[Evergreen/Agentic-Engineering\|Agentic Engineering]] — AI 协作方法论
  - [[2026-03-01_Agent_Harness_Real_Product_深度解读_v2\|Agent Harness is the Real Product]] — Harness > Model
  - [[2026-03-01_Agent_Harness_is_the_Real_Product_深度解读_v2\|Agent Harness深度对比]] — 各公司Harness架构
  - [[2026-03-01_First_Run_The_Tests_Agentic_Engineering_深度解读_v2\|First Run The Tests]] — 测试模式
  - [[2026-03-01_Hoard_Things_You_Know_Agentic_Engineering_深度解读_v2\|Hoard Things You Know]] — 知识囤积
  - [[2026-03-01_Interactive_Explanations_Agentic_Engineering_深度解读_v2\|Interactive Explanations]] — 交互式解释

### 部署
- [[Evergreen/AI-Infrastructure\|AI Infrastructure]] — AI 基础设施
- [[Evergreen/Model-Serving\|Model Serving]] — 模型服务化

---

## 📊 概念统计

```dataview
LIST
FROM "10-Knowledge/Evergreen"
WHERE file.name contains "AI" OR file.name contains "Agent" OR file.name contains "Claude" OR file.name contains "MCP"
SORT file.name ASC
```

---

## 🔗 相关 MOC

- [[MOC-Index]] — 返回 Atlas 首页
- [[../../20-Areas/Programming/MOC|AI Research MOC]] — 领域层 AI 研究
- [[../../30-Projects/README|Projects]] — AI 相关项目

---

> [!tip] 新发现的概念
> 如果发现新的 AI 概念值得记录，在 Evergreen/ 创建新笔记并添加到本 MOC。
