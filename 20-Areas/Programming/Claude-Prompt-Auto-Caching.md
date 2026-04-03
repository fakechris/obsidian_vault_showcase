---
title: "Claude Prompt Auto-Caching"
description: "自动管理缓存断点降低成本和延迟"
date: 2025-12-24
type: interpretation
tags: [Claude, Prompt-Caching, Cost-Optimization, Context-Engineering]
---

# Claude Prompt Auto-Caching

## 来源
- 原文: [[2025-12-24_Claude_Prompt_Auto-Caching]]
- 作者: Lance Martin
- 日期: 2025-12-24
- 标签: #Claude #Prompt-Caching #Cost-Optimization #Context-Engineering

## 一句话定义
Claude的Prompt Auto-Caching是一种通过自动管理缓存断点来大幅降低多轮对话成本和延迟的机制，缓存token仅需原价10%。

## 核心原理
在多轮AI交互中（尤其是Agent场景），上下文会在每次交互中重复发送。传统方式每次都需支付全额token费用。Auto-caching通过在最新的可缓存块自动设置断点，使相同内容只需计算一次prefill阶段，后续复用缓存结果，实现90%成本节约。

## 技术细节

### 启用方式
```json
{
  "cache_control": {"type": "ephemeral"},
  "messages": [...]
}
```

### 关键机制
1. **Write Point**: 在cache_control处创建所有前面内容块的加密哈希
2. **Backward Search**: 向后搜索最多20个块寻找缓存匹配
3. **Exact Match**: 内容必须完全一致（一字之差即cache miss）
4. **Auto-Movement**: 断点随对话增长自动移动到最新可缓存块

### 业界观点
- @peakji (Manus): "cache hit rate是生产AI agent的最重要指标"
- @trq212: "prompt caching对长轮次/token-heavy agent（如Claude Code）至关重要"

## 架构流程

```
[用户消息+历史+系统指令]
         ↓
[Prefill计算] → 哈希存储(工作空间作用域)
         ↓
[缓存匹配] ← 向后搜索20块
         ↓
    ┌────┴────┐
  命中      未命中
    ↓         ↓
[复用缓存]  [重新计算]
    ↓         ↓
[Decode生成] [Decode生成]
```

## 最佳实践

### DO
- 在长轮次Agent应用中启用auto-caching
- 将cache_control放在系统提示等静态内容后
- 监控cache hit rate作为关键生产指标

### DON'T
- 修改历史消息（会破坏缓存）
- 依赖缓存处理动态变化的内容
- 忽视缓存对延迟的改善效果

## 关联知识
- [[../../10-Knowledge/Evergreen/Prompt-Caching]] - 提示缓存基础概念
- [[../../40-Resources/Evergreen/Context-Engineering]] - 上下文工程设计
- [[../../10-Knowledge/Evergreen/Claude-Code]] - Claude Code实现细节
- [[../../Evergreen/Agent-Harness]] - Agent架构设计
- [[Cost-Optimization]] - AI成本优化策略

## 行动建议
1. **立即**: 审查现有Claude应用，识别适合启用auto-caching的场景
2. **短期**: 在Claude Code类工具中实现缓存监控仪表板
3. **长期**: 建立缓存友好型提示设计的内部规范

---
创建: 2026-03-30
区域: 20-Areas/Programming/
