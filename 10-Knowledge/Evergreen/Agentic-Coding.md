---
title: "Agentic Coding (智能体编程)"
type: evergreen
date: 2026-03-31
tags: [evergreen, AI, coding, software-engineering, agent, spec-driven, critique]
aliases: [Agentic-Coding, 智能体编程, AI辅助编码, Agent编码, AI-Code-Generation]
---

# Agentic Coding (智能体编程)

> **一句话定义**: Agentic Coding是利用AI Agent作为"虚拟开发者"的软件开发范式——工程师从直接编码转向编写Spec/指令并审查AI产出；但精确规范本质上等同于代码，存在两个核心误解。

---

## 核心模式: 范式转变

### 传统 vs Agentic Coding

```
传统编码:
工程师 → 直接编写代码

Agentic Coding:
工程师 → 编写Spec/指令 → AI Agent → 代码 → 工程师审查
```

**声称的价值**:
- 工程师变成"管理者"
- 聚焦高层次思考
- 外包实现细节给AI
- 提升整体工程质量

---

## 批判视角: 两个核心误解

### 误解1: 规范比代码更简单

**倡导者观点**:
> "工程师变成管理者，撰写规范文档，外包给Agent团队执行"

**批判分析** (Gabrielle Miller):

```
如果要让规范精确到能可靠生成实现:
├── 必须将规范扭曲成代码形式
├── 或高度结构化、形式化的英语
└── 本质上与写代码同等复杂度

Dijkstra引用:
"接口选择不只是劳动分工，因为跨接口协作和沟通的工作必须被加入..."

→ 规范不是免费的，有额外的沟通/协作成本
```

**OpenAI Symphony案例**:
```
声称: "从SPEC.md规范生成项目"

实际SPEC.md内容:
├── 数据库模式的散文式转储
├── 代码的散文式转储
├── "作弊表"式配置字段摘要
└── 直接的代码片段

问题: 这更像是代码的markdown形式，而非真正的规范

关键段落:
"6.4 Config Fields Summary (Cheat Sheet) - This section is intentionally redundant so a coding agent can implement the config layer quickly."
→ 这承认规范本质上是在为Agent写代码
```

**惊人发现**: Symphony规范已经是**Elixir实现代码长度的1/6**！

---

### 误解2: 规范工作比编码更有思考性

**倡导者观点**:
> "规范过滤将提高质量，促进更好的工程实践"

**批判分析**:

```
现实:
├── 规范工作应该比编码更难（需要更多思考）
├── 但行业趋势是降低和贬值劳动
├── 结果: Symphony规范读起来像AI生成的slop
└── 优化交付速度 → 无法做规范的深度思考工作
```

**深层问题**:
> 科技公司推动减少和贬值劳动，"规范工作应该更容易"的前提，导致无法做规范的深度思考工作。

---

## 精确度悖论

### 足够详细的规范 ≈ 代码

```
规范详细程度与可生成性:

低详细 ────────────────────────────────→ 高详细
   │                                      │
   ↓                                      ↓
不可靠实现                          可靠但变成代码
(需要大量猜测)                      (与写代码无异)

没有中间地带:
├── 模糊的规范 → Agent必须猜测 → 不可靠
├── 精确的规范 → 等同于代码 → 没有节省
└── 声称的"简单规范生成复杂代码"不存在
```

---

## 可靠性问题: 证据

### Symphony项目实测

```
作者用Claude Code (Haskell)构建Symphony:
├── 多个bug
├── Codex Agent静默卡死
└── 无法可靠工作
```

### YAML规范先例

```
YAML规范:
├── 极其详细
├── 广泛使用
├── 包含一致性测试套件
└── 绝大多数实现仍不完全符合规范

→ 即使是最详细的规范也无法保证可靠实现
```

---

## 核心原则: Garbage In, Garbage Out

> "There is no world where you input a document lacking clarity and detail and get a coding agent to reliably fill in that missing clarity and detail. Coding agents are not mind readers..."

**关键洞察**:
- Agent不会读心术
- 如果输入模糊，输出也模糊
- 缺失的清晰度和细节无法由Agent自动补全
- 人类的思考和决策无法被外包

---

## 与SDD的对比

| 维度 | Gabrielle Miller批评 | SDD方法 (Julián) |
|------|----------------------|------------------|
| **核心主张** | 规范替代代码是误导 | Spec→Plan→Task→Implement |
| **规范内容** | 批评伪代码式规范 | Spec层专注What (功能) |
| **实现细节** | 反对在规范中写代码 | Plan层处理How (技术) |
| **目标** | 揭露炒作 | 减少歧义 |
| **劳动价值** | 强调规范工作应该更难 | 强调开发者角色转变 |

**关键区别**:
- Gabrielle批评的是"用伪代码式规范声称替代代码"
- SDD主张的是"清晰分离What和How，减少歧义"

---

## 实践建议

### 1. 设定期望

AI适合辅助，不适合完全替代。

### 2. 投资思考

Spec的价值在于强迫深度思考——如果做不到，不如直接写代码。

### 3. 质量第一

> "Garbage in, garbage out"原则适用

### 4. 区分规范类型

```
检查你的规范:
├── 是否包含伪代码或代码片段?
├── 读起来是否像"markdown格式的代码"?
├── 是否声称"简单规范生成复杂代码"?
└── 如果是 → 可能是误导性的
```

---

## 关键数据

| 数字 | 含义 |
|------|------|
| **1/6** | Symphony SPEC长度 vs Elixir实现代码长度 |
| **6.4** | "Cheat Sheet"章节 (故意冗余以便Agent实现) |
| **2** | 核心误解数量 |

---

## 关联概念

- [[Spec-Driven-Development]] — SDD方法论（与批判视角对比）
- [[Claude-Code]] — Agentic Coding的工具实现
- [[Coding-Agent]] — 编程Agent的技术细节
- [[AI-Code-Generation]] — AI代码生成技术
- [[Precision-Paradox]] — 精确度悖论

---

## 来源引用

- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-18_A_sufficiently_detailed_spec_is_code_深度解读]] — Gabrielle Miller的批判分析

---

*创建于 2026-03-18，补充于 2026-03-31，精读深度解读提取*
