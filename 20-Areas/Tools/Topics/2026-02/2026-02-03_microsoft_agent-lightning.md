---
title: "microsoft/agent-lightning: Agent 强化学习训练框架 (16.5k stars)"
github: "https://github.com/microsoft/agent-lightning"
owner: microsoft
repo: agent-lightning
date: 2026-02-03
batch_date: 2026-02-03
type: github-project
tags: [github, agent, reinforcement-learning, training, microsoft, rl]
pinboard_tags: [agent, microsoft]
source_used: github-readme-extract
source_url: "https://github.com/microsoft/agent-lightning"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# microsoft/agent-lightning: Agent 强化学习训练框架

## 一句话概述

Agent Lightning 是微软开源的 Agent 强化学习训练框架，支持零代码改动优化任何 Agent 框架（LangChain、OpenAI Agent SDK、AutoGen 等），通过 Reinforcement Learning、Automatic Prompt Optimization、Supervised Fine-tuning 等算法持续改进 Agent 性能。

## 项目定位

**目标用户**:
- 需要优化 Agent 性能的 AI 开发者
- 研究 Agent RL 的研究者
- 构建生产级 Agent 系统的工程师

**解决的问题**:
- **Agent 性能难以优化**: 传统方式需要频繁修改代码和提示词
- **训练与推理割裂**: 现有方案需要重写 Agent 架构
- **多 Agent 系统优化难**: 复杂系统难以统一优化
- **缺乏持续学习**: Agent 无法从执行中自动改进

**使用场景**:
- 零代码改动优化现有 Agent
- 多 Agent 系统中选择性优化特定 Agent
- Agent 强化学习研究与实验
- 生产环境 Agent 持续改进

**与同类项目差异**:
- **零代码改动**: 几乎无需修改现有 Agent 代码
- **框架无关**: 支持任何 Agent 框架或无框架
- **多算法支持**: RL、Prompt 优化、监督微调
- **微软官方**: Microsoft Research 出品，企业级质量
- **GPU-poor 友好**: 无需大量 GPU 资源即可训练

## README 中文简介

**Agent Lightning**⚡ - 点亮 AI agents 的终极训练器

**核心特性**:
- 几乎**零代码改动**将 Agent 变成可优化的野兽
- 支持**任何 Agent 框架** (LangChain、OpenAI Agent SDK、AutoGen、CrewAI、Microsoft Agent Framework) 或**无框架** (Python OpenAI)
- 可选择性优化多 Agent 系统中的特定 Agent
- 支持强化学习、自动提示词优化、监督微调等算法

**安装**:
```bash
pip install agentlightning

# 最新夜间构建
pip install --upgrade --index-url https://test.pypi.org/simple/ \
  --extra-index-url https://pypi.org/simple/ --pre agentlightning
```

**快速开始**:
参见 [文档网站](https://microsoft.github.io/agent-lightning/) 和 [examples/](examples/)

**架构**:
Agent Lightning 最小化移动部件，让你专注于想法而非管道：

```
Agent 照常运行 ──▶ agl.emit_xxx() helper ──▶ LightningStore
                                                    │
                                                    ▼
算法 (你选择或编写) ◀── 任务、资源、追踪同步 ──▶ Trainer
    │
    └─▶ 更新资源 (提示词模板、策略权重) ──▶ 推理引擎更新
```

**关键组件**:
- **LightningStore**: 中心枢纽，同步任务、资源、追踪
- **agl.emit_xxx()**: 轻量级 helper，收集 prompt、tool call、reward
- **Algorithm**: 读取 spans、学习、发布更新资源
- **Trainer**: 流式传输数据集、 ferry 资源、更新推理引擎

**研究文章**:
| 日期 | 主题 |
|------|------|
| 2025-12-17 | [Trajectory Level Aggregation 加速训练](https://agentlightning.com/blog) |
| 2025-11-04 | [用 Tinker 调优任何 AI Agent](https://medium.com/...) |
| 2025-10-22 | [通过 OpenAI Compatible API 返回 Token IDs](https://blog.vllm.ai/...) |
| 2025-08-11 | [用 RL 训练 Agent 写 SQL 和自我纠错](https://medium.com/...) |
| 2025-08-05 | [Agent Lightning: 用 RL 训练任何 AI Agent](https://arxiv.org/abs/2508.03680) |

**社区项目**:
- **DeepWerewolf**: AgentScope + Agent Lightning 的狼人杀 RL 训练
- **AgentFlow**: Flow-GRPO 算法的长时程任务框架
- **Youtu-Agent**: 验证高达 128 GPU RL 训练，数学/代码/搜索能力

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 零代码改动 | emit_xxx() helper 轻量集成 | README | 高 |
| 框架无关 | 支持任何 Agent 框架或无框架 | README | 高 |
| 多算法支持 | RL、Prompt 优化、监督微调 | README | 高 |
| 选择性优化 | 多 Agent 系统中优化特定 Agent | README | 高 |
| LightningStore | 任务/资源/追踪同步中心 | README | 高 |
| 128 GPU 扩展 | 社区验证大规模训练 | README | 高 |
| 微软官方 | Microsoft Research 项目 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Agent Lightning 架构                          │
│           (Agent 强化学习训练框架)                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Agent 层 (你的 Agent)                │  │
│  │                                                  │  │
│  │   ┌────────────────────────────────────────┐   │  │
│  │   │           任何 Agent 框架            │   │  │
│  │   │                                          │   │  │
│  │   │  • LangChain                              │   │  │
│  │   │  • OpenAI Agent SDK                       │   │  │
│  │   │  • AutoGen                                │   │  │
│  │   │  • CrewAI                                 │   │  │
│  │   │  • Microsoft Agent Framework              │   │  │
│  │   │  • 或无框架 (Python OpenAI)              │   │  │
│  │   │                                          │   │  │
│  │   │  ↓ 添加 agl.emit_xxx() helper            │   │  │
│  │   └────────────────────────────────────────┘   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              LightningStore 层                   │  │
│  │                                                  │  │
│  │   中心枢纽，同步:                                │  │
│  │   • Tasks (任务)                                │  │
│  │   • Resources (资源)                            │  │
│  │   • Traces (追踪/Spans)                         │  │
│  │                                                  │  │
│  │   prompt ──▶ tool call ──▶ reward            │  │
│  │      │           │            │                │  │
│  │      └───────────┴────────────┘                │  │
│  │                  ↓                             │  │
│  │            Structured Spans                    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              算法层                              │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────┐  │  │
│  │   │  RL 算法     │ Prompt 优化  │ 监督微调 │  │  │
│  │   ├──────────────┼──────────────┼──────────┤  │  │
│  │   │ Reinforcement│ Automatic   │ Supervised│  │  │
│  │   │ Learning     │ Prompt      │ Fine-tuning│  │  │
│  │   │              │ Optimization│          │  │  │
│  │   └──────────────┴──────────────┴──────────┘  │  │
│  │                                                  │  │
│  │   • 读取 spans                                   │  │
│  │   • 学习                                         │  │
│  │   • 发布更新资源                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Trainer 层                          │  │
│  │                                                  │  │
│  │   • 流式传输数据集到 Runners                     │  │
│  │   • 在 Store 和 Algorithm 之间 ferry 资源       │  │
│  │   • 更新 Inference Engine                        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输出层                                │  │
│  │                                                  │  │
│  │   更新后的资源:                                  │  │
│  │   • 精炼的提示词模板                              │  │
│  │   • 新的策略权重                                │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| Agent 集成 | `agentlightning/` | Agent 框架集成 | 用户层 |
| Dashboard | `dashboard/` | 训练监控面板 | 可视化 |
| 示例 | `examples/` | 使用示例 | 参考 |
| 文档 | `docs/` | 文档网站 | 参考 |
| 测试 | `tests/` | 测试套件 | 质量保证 |
| Docker | `docker/` | 容器化部署 | 部署 |

## 运行与开发方式

**安装**:
```bash
pip install agentlightning
```

**最新构建**:
```bash
pip install --upgrade --index-url https://test.pypi.org/simple/ \
  --extra-index-url https://pypi.org/simple/ --pre agentlightning
```

**快速开始**:
```bash
# 查看文档
https://microsoft.github.io/agent-lightning/

# 查看示例
ls examples/
```

**开发设置**:
```bash
# 克隆仓库
git clone https://github.com/microsoft/agent-lightning.git
cd agent-lightning

# 安装开发依赖
pip install -e ".[dev]"

# 运行测试
pytest tests/
```

**社区项目使用**:
- **DeepWerewolf**: 狼人杀 RL 训练案例
- **AgentFlow**: 长时程任务 Flow-GRPO
- **Youtu-Agent**: 128 GPU 大规模训练验证

## 外部接口

**Python API**:
| 函数/类 | 功能 |
|---------|------|
| `agl.emit_xxx()` | 记录 prompt、tool call、reward |
| `LightningStore` | 任务/资源/追踪同步中心 |
| `Trainer` | 训练协调器 |

**算法选择**:
| 算法 | 场景 |
|------|------|
| Reinforcement Learning | 策略优化 |
| Automatic Prompt Optimization | 提示词改进 |
| Supervised Fine-tuning | 行为克隆 |

**CI 状态**:
| 工作流 | 状态 |
|--------|------|
| CPU Tests | ✅ |
| Full Tests | ✅ |
| UI Tests | ✅ |
| Examples Integration | ✅ |
| Latest Dependency | ✅ |
| Legacy Examples | ✅ |

## 数据流 / 控制流

```
Agent 运行
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 数据收集                                                │
│    • agl.emit_prompt()                                     │
│    • agl.emit_tool_call()                                  │
│    • agl.emit_reward()                                     │
│    → Structured Spans                                       │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. LightningStore 同步                                     │
│    • Tasks (任务状态)                                      │
│    • Resources (资源配置)                                  │
│    • Traces (执行追踪)                                     │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 算法处理 (可选择)                                       │
│    ├─▶ RL 算法: 策略梯度优化                               │
│    ├─▶ Prompt 优化: 自动改进提示词                        │
│    └─▶ 监督微调: 从示范学习                               │
│    → 生成更新资源                                         │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 4. Trainer 协调                                            │
│    • 流式传输数据集                                        │
│    • ferry 资源                                            │
│    • 更新推理引擎                                          │
└────────────────────────────────────────────────────────────┘
    ↓
Agent 性能提升 (循环继续)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (81.8%) | 高 |
| TypeScript | Dashboard (15.6%) | 高 |
| PyTorch | RL 训练 | 高 |
| Docker | 部署 | 高 |
| GitHub Actions | CI/CD | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 文档网站 + 示例 + 论文 | 高 |
| 上手难度 | 中 | 需要理解 RL 概念 | 中 |
| 架构复杂度 | 高 | 涉及 RL、分布式训练 | 高 |
| 外部依赖 | 中 | 依赖 LLM API | 中 |
| Stars | 高 | 16.5k stars |
| 企业背书 | 高 | Microsoft Research | 高 |

**注意事项**:
- 需要理解强化学习基础概念
- 大规模训练需要 GPU 资源
- 社区项目验证了 128 GPU 扩展性
- 微软官方项目，长期支持有保障

## 关联概念

- [[Reinforcement-Learning]] - 强化学习
- [[Agent-Training]] - Agent 训练
- [[LLM-Fine-Tuning]] - LLM 微调
- [[Prompt-Optimization]] - 提示词优化
- [[Microsoft-Research]] - 微软研究院
- [[Multi-Agent]] - 多 Agent 系统

---

> 来源: [GitHub](https://github.com/microsoft/agent-lightning) | 置信度: 基于 GitHub README
> 👤 **作者**: microsoft (Microsoft Research)
> ⭐ **Stars**: 16.5k
> 📄 **论文**: [arXiv:2508.03680](https://arxiv.org/abs/2508.03680)
> 🏢 **组织**: Microsoft Research
> 🔗 **文档**: https://microsoft.github.io/agent-lightning/
