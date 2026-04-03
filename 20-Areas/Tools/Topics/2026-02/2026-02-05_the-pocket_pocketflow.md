---
title: "The-Pocket/PocketFlow: 100行极简 LLM 框架 (10.3k stars)"
github: "https://github.com/The-Pocket/PocketFlow"
owner: The-Pocket
repo: PocketFlow
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, llm, framework, python, minimalist, agent]
pinboard_tags: [llm, framework, python]
source_used: github-readme-extract
source_url: "https://github.com/The-Pocket/PocketFlow"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# The-Pocket/PocketFlow: 100行极简 LLM 框架

## 一句话概述

PocketFlow 是一个仅 100 行代码的极简 LLM 框架，零依赖、零厂商锁定，支持 (Multi-)Agents、Workflow、RAG 等，让 AI Agent 构建 Agent，生产力提升 10 倍。

## 项目定位

**目标用户**:
- 寻求极简 LLM 框架的开发者
- 厌倦了臃肿框架的工程师
- 需要无厂商锁定的团队
- 希望快速原型 AI Agent 的用户

**解决的问题**:
- **框架臃肿**: LangChain 等框架过于复杂，学习曲线陡峭
- **厂商锁定**: 依赖特定提供商难以迁移
- **依赖过多**: 大量依赖导致维护困难
- **Agent 构建效率低**: 传统方式构建 Agent 周期长

**使用场景**:
- 快速原型 LLM 应用
- 学习 LLM 框架核心原理
- 构建无依赖的 Agent 系统
- AI Agent 自动构建 Agent（元编程）

**与同类项目差异**:
- **极致精简**: 仅 100 行代码
- **零依赖**: 无外部依赖
- **零厂商锁定**: 不绑定任何 LLM 提供商
- **多语言支持**: Python、TypeScript、Java、C++、Go、Rust、PHP
- **Agentic Coding**: AI Agent 构建 Agent，10 倍生产力

## README 中文简介

**Pocket Flow** - 100 行极简 LLM 框架

**English | 中文 | Español | 日本語 | Deutsch | Русский | Português | Français | 한국어**

**轻量**: 仅 100 行。零膨胀、零依赖、零厂商锁定。

**表达力强**: 您想要的一切 —— (多)Agent、工作流、RAG 等等。

**Agentic Coding**: 让 AI Agent（如 Cursor AI）构建 Agent —— 生产力提升 10 倍！

**快速开始**:

安装：`pip install pocketflow`

或直接复制源代码（仅 100 行）。

了解更多：视频教程 和 文档

🎉 加入 Discord 与使用 Pocket Flow 的其他开发者连接！

🎉 Pocket Flow 现在有 TypeScript、Java、C++、Go、Rust 和 PHP 版本！

**为什么选 Pocket Flow?**

当前 LLM 框架过于臃肿……您只需要 100 行就能实现 LLM 框架！

**对比**:

| 框架 | 抽象 | 应用特定包装 | 厂商特定包装 | 代码行数 | 大小 |
|------|------|--------------|--------------|----------|------|
| LangChain | 是 | 是 | 是 | 多 | 大 |
| LlamaIndex | 是 | 是 | 是 | 多 | 大 |
| PocketFlow | 极简 | 无 | 无 | 100 行 | 极小 |

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 极简代码 | 仅 100 行 | README | 高 |
| 零依赖 | 无外部依赖 | README | 高 |
| 零锁定 | 无厂商绑定 | README | 高 |
| 多 Agent | 支持多 Agent 系统 | README | 高 |
| Workflow | 工作流支持 | README | 高 |
| RAG | 检索增强生成 | README | 高 |
| 多语言 | 9 种语言版本 | README | 高 |
| Agentic Coding | AI 构建 Agent | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              PocketFlow 架构                                 │
│           (100行极简 LLM 框架)                               │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心层 (100 行)                       │  │
│  │                                                  │  │
│  │   • 节点抽象 (Node)                              │  │
│  │   • 流抽象 (Flow)                                │  │
│  │   • 代理抽象 (Agent)                             │  │
│  │   • 共享存储 (Shared Store)                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Multi-Agent  │ Workflow     │ RAG          ││  │
│  │   │ (多代理)     │ (工作流)     │ (检索增强)   ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ 工具调用     │ 批处理       │ 流式处理     ││  │
│  │   │ (Tools)      │ (Batch)      │ (Streaming)  ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              多语言层                              │  │
│  │                                                  │  │
│  │   Python | TypeScript | Java | C++ | Go | Rust | PHP │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心 | `pocketflow/` | 100 行核心代码 | 核心 |
| 食谱 | `cookbook/` | 示例和教程 | 示例 |
| 测试 | `tests/` | 测试套件 | 质量 |
| 工具 | `utils/` | 工具函数 | 工具 |

## 运行与开发方式

**安装**:
```bash
pip install pocketflow
```

**或复制源码**:
仅 100 行，可直接复制到项目。

**快速开始**:
```python
from pocketflow import Node, Flow

# 定义节点
class MyNode(Node):
    def prep(self, shared):
        return shared.get("input")

    def exec(self, prep_res):
        return f"Processed: {prep_res}"

    def post(self, shared, prep_res, exec_res):
        shared["output"] = exec_res
        return "default"

# 创建流
flow = Flow(start=MyNode())

# 运行
shared = {"input": "Hello"}
flow.run(shared)
print(shared["output"])  # Processed: Hello
```

**开发**:
```bash
# 克隆仓库
git clone https://github.com/The-Pocket/PocketFlow.git
cd PocketFlow

# 安装
pip install -e .

# 测试
python -m pytest
```

## 外部接口

**核心类**:
| 类 | 功能 |
|----|------|
| `Node` | 基本节点抽象 |
| `Flow` | 流控制 |
| `Agent` | Agent 抽象 |
| `BatchFlow` | 批处理流 |
| `ParallelFlow` | 并行流 |

**节点生命周期**:
```python
class MyNode(Node):
    def prep(self, shared):      # 准备数据
        pass

    def exec(self, prep_res):    # 执行逻辑
        pass

    def post(self, shared, prep_res, exec_res):  # 后置处理
        pass
```

## 数据流 / 控制流

```
Shared Store (共享数据)
    ↓
Node.prep() → 准备数据
    ↓
Node.exec() → 执行核心逻辑
    ↓
Node.post() → 更新 Shared Store
    ↓
下一个节点 / 结束
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| TypeScript | 多语言版本 | 高 |
| Java | 多语言版本 | 高 |
| C++ | 多语言版本 | 高 |
| Go | 多语言版本 | 高 |
| Rust | 多语言版本 | 高 |
| PHP | 多语言版本 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 视频教程、文档、多语言 | 高 |
| 上手难度 | 低 | 100 行代码，易于理解 | 低 |
| 架构复杂度 | 低 | 极简设计 | 低 |
| 外部依赖 | 无 | 零依赖 | 极低 |
| Stars | 高 | 10.3k stars | 高 |
| 维护状态 | 高 | 活跃社区，Discord 支持 | 高 |

**与其他框架对比**:

| 框架 | 代码量 | 依赖 | 厂商锁定 | 学习曲线 |
|------|--------|------|----------|----------|
| LangChain | 大 | 多 | 有 | 陡峭 |
| LlamaIndex | 大 | 多 | 有 | 陡峭 |
| PocketFlow | 100行 | 无 | 无 | 平缓 |

**优势**:
- 快速理解 LLM 框架核心
- 无依赖，易于嵌入
- 自由扩展到任意 LLM 提供商
- 适合教学和学习

## 关联概念

- [[LLM-Framework]] - 大语言模型框架
- [[LangChain]] - 主流 LLM 框架
- [[LlamaIndex]] - RAG 框架
- [[Multi-Agent]] - 多代理系统
- [[Workflow]] - 工作流
- [[RAG]] - 检索增强生成
- [[Agentic-Coding]] - 代理编程
- [[Cursor-AI]] - Cursor AI 编辑器

---

> 来源: [GitHub](https://github.com/The-Pocket/PocketFlow) | 置信度: 基于 GitHub README
> 👤 **作者**: The Pocket
> ⭐ **Stars**: 10.3k
> 🔗 **官网**: [GitHub](https://github.com/The-Pocket/PocketFlow)
> 💬 **社区**: [Discord](https://discord.gg/pocketflow)
> 📜 **许可证**: MIT
