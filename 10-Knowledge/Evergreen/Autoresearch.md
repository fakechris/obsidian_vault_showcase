---
title: "Autoresearch (自主研究)"
description: "让AI agent自主运行研究实验的框架，关键挑战是防止Agent漂移（drift）"
type: evergreen
date: 2026-03-17
tags:
  - concept
  - autoresearch
  - ai-agent
  - research-automation
  - agent-drift
aliases:
  - 自主研究
  - Agent研究
  - AI-Research-Loop
---

# Autoresearch (自主研究)

> **定义**: 让AI agent自主提出实验方案、执行、测试、记录结果、迭代优化的研究自动化框架。

---

## 核心流程

```
输入: 目标 + 指标 + 代码库
  ↓
读取程序 → 提出修改 → 提交 → 训练 → 评估
  ↓
更好? 保留 : 回滚
  ↓
重复
```

---

## 关键挑战: Agent Drift

**问题**: Agent在几小时内"跑偏"，开始自己的side quest。

**解决方案**:
- 严格的scope设计
- 频繁的验证检查点
- 环境隔离
- 主动重新引导

---

## 核心发现

1. **趋同**: 不同Agent找到相同答案 → 搜索景观有真实结构
2. **提案质量 > 速度**: GPT-5.4 (67%接受率) 比 Spark (17%) 总成本更低
3. **环境 > 模型**: 严格环境成功，宽松环境漂移

---

## 成功要素

```
✅ 可测量目标
✅ 严格验证gate
✅ 一次一个实验
✅ 环境隔离
✅ 频繁检查点
```

---

## 关联知识

- [[2026-03-17_How_to_stop_autoresearch_loop_from_cheating_深度解读|原文深度解读]]
- [[Agent-Drift]]
- [[Error-Analysis]]
- [[Model-Compression]]

---

> **引用**: "瓶颈不是智能，是周围的一切。" — Sarah Chieng
