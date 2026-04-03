---
title: "AlexsJones/llmfit: LLM 硬件适配工具 (20.8k stars)"
github: "https://github.com/AlexsJones/llmfit"
owner: AlexsJones
repo: llmfit
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, rust, llm, hardware, tui, cli]
pinboard_tags: [llm, hardware, rust]
source_used: github-readme-extract
source_url: "https://github.com/AlexsJones/llmfit"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# AlexsJones/llmfit: LLM 硬件适配工具

## 一句话概述

llmfit 是一个终端工具，根据系统 RAM、CPU 和 GPU 为 LLM 模型"量体裁衣"，检测硬件配置，从质量、速度、适配度和上下文维度评分，告诉您哪些模型能在您的机器上良好运行。

## 项目定位

**目标用户**:
- 希望在本地运行 LLM 但不确定模型兼容性的用户
- 需要评估硬件 LLM 运行能力的开发者
- 寻求模型性能优化的工程师
- 多 GPU 环境的管理员

**解决的问题**:
- **模型选择困难**: 数百个模型不知哪个适合自己的硬件
- **资源不匹配**: 下载后发现模型无法运行或运行缓慢
- **量化选择复杂**: 不同量化级别难以选择
- **多硬件支持**: 需要支持 CPU、GPU、多 GPU 配置
- **运行时选择**: 需要在 Ollama、llama.cpp、MLX 等运行时中选择

**使用场景**:
- 本地 LLM 部署前硬件评估
- 新模型兼容性检查
- 多 GPU 环境配置
- 边缘设备模型选择

**与同类项目差异**:
- **硬件检测自动**: 自动检测 RAM、CPU、GPU
- **多维度评分**: 质量、速度、适配度、上下文四维度
- **运行时支持广**: Ollama、llama.cpp、MLX、Docker Model Runner、LM Studio
- **交互式 TUI**: 默认 TUI 模式，支持经典 CLI
- **MoE 架构支持**: 支持 Mixture of Experts 模型

## README 中文简介

**llmfit** - 为您的硬件找到合适的 LLM 模型

**数百个模型和提供商。一条命令找到适合您硬件的。**

一个根据系统 RAM、CPU 和 GPU 为 LLM 模型"量体裁衣"的终端工具。检测您的硬件，从质量、速度、适配度和上下文维度为每个模型评分，告诉您哪些模型能在您的机器上真正良好运行。

**附带功能**:
- 交互式 TUI（默认）
- 经典 CLI 模式
- 支持多 GPU 设置
- MoE 架构支持
- 动态量化选择
- 速度估计
- 本地运行时提供商（Ollama、llama.cpp、MLX、Docker Model Runner、LM Studio）

**相关项目**:
- **sympozium** — 在 Kubernetes 中管理 Agent
- **llmserve** — 简单的本地 LLM 模型服务 TUI

**安装**:

**Windows**:
```bash
scoop install llmfit
```

**macOS / Linux - Homebrew**:
```bash
brew install llmfit
```

**macOS / Linux - 快速安装**:
```bash
curl -fsSL https://llmfit.axjns.dev/install.sh | sh
```
从 GitHub 下载最新版本二进制文件并安装到 /usr/local/bin（或 ~/.local/bin 如果没有 sudo）。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 硬件检测 | 自动检测 RAM/CPU/GPU | README | 高 |
| 模型评分 | 质量/速度/适配度/上下文 | README | 高 |
| TUI 界面 | 交互式终端 UI | README | 高 |
| 多 GPU | 多 GPU 配置支持 | README | 高 |
| MoE 支持 | Mixture of Experts | README | 高 |
| 动态量化 | 自动量化选择 | README | 高 |
| 速度估计 | 运行速度预测 | README | 高 |
| 多运行时 | Ollama/llama.cpp/MLX 等 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              llmfit 架构                                     │
│           (LLM 硬件适配工具)                                 │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              界面层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ TUI          │ CLI          │              │  │
│  │   │ (交互式)     │ (经典)       │              │  │
│  │   │ (默认)       │ (脚本化)     │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心引擎层                            │  │
│  │                                                  │  │
│  │   • 硬件检测                                     │  │
│  │   • 模型数据库                                   │  │
│  │   • 评分算法                                     │  │
│  │   • 量化计算                                     │  │
│  │   • 速度预测                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              运行时适配层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Ollama       │ llama.cpp    │ MLX          ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ Docker Model │ LM Studio    │              ││  │
│  │   │ Runner       │              │              ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心 | `llmfit-core/` | 核心引擎 | 核心 |
| 桌面 | `llmfit-desktop/` | 桌面应用 | 应用 |
| TUI | `llmfit-tui/` | 终端界面 | 核心 |
| Web | `llmfit-web/` | Web 界面 | 扩展 |
| Skill | `skills/llmfit-advisor/` | Claude Code Skill | 扩展 |

## 运行与开发方式

**快速安装**:
```bash
# macOS / Linux
curl -fsSL https://llmfit.axjns.dev/install.sh | sh

# 或 Homebrew
brew install llmfit

# Windows
scoop install llmfit
```

**使用**:
```bash
# 启动 TUI（默认）
llmfit

# CLI 模式
llmfit --cli

# 查看帮助
llmfit --help
```

**开发**:
```bash
# 克隆仓库
git clone https://github.com/AlexsJones/llmfit.git
cd llmfit

# 构建 (Rust)
cargo build --release

# 运行
cargo run
```

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `llmfit` | 启动 TUI |
| `llmfit --cli` | 经典 CLI 模式 |
| `llmfit --list` | 列出模型 |
| `llmfit --check <model>` | 检查特定模型 |

**评分维度**:
| 维度 | 说明 |
|------|------|
| Quality | 模型质量 |
| Speed | 运行速度 |
| Fit | 硬件适配度 |
| Context | 上下文长度 |

## 数据流 / 控制流

```
硬件检测
    ↓
模型数据库查询
    ↓
多维度评分计算
    ↓
结果展示 (TUI/CLI)
    ↓
用户选择模型
    ↓
运行时建议
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Rust | 主要语言 | 高 |
| Ratatui | TUI 框架 | 中 |
| CUDA | GPU 检测 | 中 |
| Metal | Apple GPU | 中 |
| Vulkan | 跨平台 GPU | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 多语言 README | 高 |
| 上手难度 | 低 | 一键安装 | 低 |
| 架构复杂度 | 中 | 硬件检测 + 评分 | 中 |
| 外部依赖 | 中 | 需要硬件信息 | 中 |
| Stars | 高 | 20.8k stars | 高 |
| 维护状态 | 高 | 活跃开发 | 高 |

**注意事项**:
- 硬件检测需要系统权限
- GPU 评分可能因驱动而异
- 速度估计基于理论计算

**评分解读**:
- **Quality**: 模型输出质量评分
- **Speed**: tokens/second 预测
- **Fit**: 内存占用的适配程度
- **Context**: 最大上下文长度支持

## 关联概念

- [[LLM]] - 大语言模型
- [[Ollama]] - 本地 LLM 运行时
- [[llama.cpp]] - C++ LLM 实现
- [[MLX]] - Apple ML 框架
- [[GPU-Computing]] - GPU 计算
- [[Model-Quantization]] - 模型量化
- [[MoE]] - Mixture of Experts
- [[TUI]] - Terminal User Interface

---

> 来源: [GitHub](https://github.com/AlexsJones/llmfit) | 置信度: 基于 GitHub README
> 👤 **作者**: AlexsJones
> ⭐ **Stars**: 20.8k
> 🔗 **官网**: [GitHub](https://github.com/AlexsJones/llmfit)
> 📜 **许可证**: MIT
