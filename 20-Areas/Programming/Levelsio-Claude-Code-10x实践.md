# Levelsio Claude Code 10x产出实践

## 来源
- 原文: [[../../50-Inbox/03-Processed/2026-02-02_Levelsio_Claude_Code_Sprint]]
- 作者: @levelsio
- 日期: 2026-02-02
- 标签: #Claude-Code #Indie-Hacker #Productivity #Shipping #AI-Coding

## 一句话定义
Levelsio通过Claude Code的bypass权限模式和生产服务器直接开发，实现一周10倍产出的独立开发者案例。

## 核心配置

### Bypass权限模式
```bash
c() { IS_SANDBOX=1 claude --dangerously-skip-permissions "$@"; }
```

**效果**:
- 无需每次确认权限，消除上下文切换成本
- 直接在生产服务器运行，消除部署等待
- 代码完成→刷新页面→测试，反馈循环极短

### 工作模式转变

| 阶段 | 模式 | 速度 |
|------|------|------|
| 之前 | 不信任AI，每一步检查 | 慢 |
| 现在 | 创建测试，让AI自由运行，测试验证 | 10x |

## 一周产出清单

### Photo AI
- 新建图像查看器和移动端查看器
- 批量remix、多照片导入、画廊模型筛选
- 安全大修: 淘汰?hash=登录，迁移到session tokens
- 修复Google登录循环、多模型选择、talking scripts
- 自定义音频上传、动态模型选择器

### Interior AI
- 复活[Add furniture]功能（6个月前开始，图像模型现在足够好）
- 自定义风格上传、自建Gaussian Splat 3D查看器
- /remove_bg端点、World Labs API迁移
- .skp文件支持、油漆颜色遮罩、空房间按钮

### Nomads
- 启动AI生成周刊newsletter
- 个人资料编辑modal、数百个新标签
- TikTok/YouTube链接、状态栏、服务端API追踪

### Hoodmaps
- 复活write mode（之前只读几年因为数据库损坏）
- heatmap模式（5万+标签情感评分）
- 修复根本原因: PRAGMA应为WAL导致标签未入库
- 设置Claude Code Telegram bot实时修改

### MAKE book + Pieter.com + Remote OK + Hotelist
- 自动ePub/PDF生成器、Kindle Wikipedia阅读器
- Chatbase AI客服机器人、酒店URL修复

## 关键洞察

### 1. 速度超越创意成为瓶颈
> "我现在交付速度比我产生新想法的速度还快"

真正瓶颈从"能多快交付"转变为"能多快产生有价值的创意"。

### 2. 心理上下文窗口成为新限制
能同时在脑中保持多少功能、bug、项目并行推进。

### 3. 信任vs检查的平衡点
- 朋友使用Claude Code慢是因为仍检查每一步
- 更好的方式: 创建测试→让AI自由运行→验证测试结果
- 99%情况下AI直接做对，然后要求进一步优化

### 4. 生产环境开发的飞轮效应
- 无需等待部署（即使之前只需3秒，累积起来也是成本）
- 代码完成→刷新→测试，这是Levelsio的工作方式

## 关联知识
- [[../../10-Knowledge/Evergreen/Claude-Code]] - Claude Code使用模式
- [[Indie-Hacker]] - 独立开发者方法论
- [[AI-Coding-Productivity]] - AI编程生产力
- [[Shipping-Fast]] - 快速交付实践

## 行动建议
1. **立即**: 设置bypass权限alias，消除权限确认摩擦
2. **短期**: 建立测试驱动的工作流，用测试代替人工检查
3. **长期**: 重新设计创意产生流程，匹配新的开发速度

---
创建: 2026-03-30
区域: 20-Areas/Programming/
