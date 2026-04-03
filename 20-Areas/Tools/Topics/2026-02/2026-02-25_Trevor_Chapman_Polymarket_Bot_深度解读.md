---
title: Trevor Chapman Polymarket Bot - 深度解读
author: "@jtrevorchapman"
source: https://x.com/jtrevorchapman/status/2027136529378718114
date: 2026-02-25
type: analysis
tags:
  - tool
  - Polymarket
  - trading-bot
  - quant
  - tool/AI
  - prediction-market
related:
  - "[[2026-02-25_Trevor_Chapman_Polymarket_Bot]]"
---

# 深度解读

## 核心观点

Trevor Chapman 分享了他在 Polymarket BTC 15 分钟合约上的自动交易系统架构：一个三层置信度计算系统——**Memory（历史先验）→ Signals（实时信号投票）→ Defense（风险抑制）**。18 小时只有两次亏损。核心洞见：**防御产生 alpha，而非进攻。信号决定方向，哨兵决定仓位。**

## 重要细节

- **Layer 1 Session Memory**：扫描最近 30+ 个已完结 session，计算"当过去的 session 长这样时，哪边赢了"——得到一个方向性先验偏差
- **Layer 2 Signal Voting**：每秒 8-12 个信号规则独立投票（YES/NO + 置信度 0-100%）。信号来源包括 Chainlink oracle 偏差、Binance 60s 动量、5m CVD 买压等。加权多数票决定方向
- **Layer 3 Defense/Sentinel**：5 个风控问题决定仓位缩放：Binance 资金流是否同意？Oracle 离 PTB 多远？剩余时间多少？Session 波动多大（5+次反转=混乱）？利润空间多少？
- **关键设计**：65% 置信度的信号不等于 65% 仓位。经过 sentinel 抑制后可能变成 $1.50（从 $5），或在所有风控绿灯时放大到 $7
- **数据驱动改进**：记录所有数据，从指标中找到"晚期反转"的前兆信号来优化对冲逻辑

## 关联知识

- [[2026-03-08_预测市场交易员数学101_深度解读]] — 预测市场的数学基础
- [[2026-01-30_Polymarket_Math_Roadmap_解读]] — 量化套利的工程实现
- [[2026-02-28_Quant_Desk_Simulation_解读]] — 量化模拟技术栈
- [[20-Areas/AI-Research/Topics/2026-02/2026-02-23_Dexter-Financial-Agent_深度解读]] — 另一个金融 Agent 系统

## 行动建议

1. **交易系统设计中把"信号"和"仓位管理"分开**——信号负责方向判断，sentinel 负责风险控制
2. **给风控规则加复合评分而非简单阈值**——5 个因子的组合比单一指标更稳健
3. **记录所有交易数据**——"几乎总有可从指标推导的前兆信号"来优化策略
4. **用历史 session 的胜率作为先验**——贝叶斯思维的自然应用

## 反思

这个三层架构设计很精巧，特别是"Defense generates alpha, not offense"这个洞见——在预测市场这种高噪音环境中，风控能力比信号能力更重要。但需要注意 BTC 15 分钟合约是非常特殊的品种（高频、可量化），这个系统不一定适用于政治/事件类合约（信息不对称更严重，数据源不同）。18 小时的回测窗口也太短，需要更长时间验证。
