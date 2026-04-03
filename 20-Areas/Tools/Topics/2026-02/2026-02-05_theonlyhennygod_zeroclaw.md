---
title: "theonlyhennygod/zeroclaw: 零开销个人 AI 助手 (66 stars)"
github: "https://github.com/theonlyhennygod/zeroclaw"
owner: theonlyhennygod
repo: zeroclaw
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, rust, ai, assistant, embedded, harvard]
pinboard_tags: [rust, ai, assistant]
source_used: github-readme-extract
source_url: "https://github.com/theonlyhennygod/zeroclaw"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# theonlyhennygod/zeroclaw: 零开销个人 AI 助手

## 一句话概述

ZeroClaw 是一个由哈佛、MIT 和 Sundai.Club 社区的学生和成员构建的超轻量级个人 AI 助手，100% Rust，$10 硬件、<5MB RAM，比 OpenClaw 少 99% 内存，比 Mac mini 便宜 98%。

## 项目定位

**目标用户**:
- 寻求极致轻量级 AI 助手的用户
- 嵌入式和边缘设备开发者
- 学生和研究者
- Rust 语言爱好者

**解决的问题**:
- **资源消耗过高**: 主流 AI 助手需要大量内存和计算
- **成本昂贵**: 运行 AI 助手需要高端硬件
- **架构不透明**: 许多项目基于现有框架修改
- **学习效率**: 学生项目需要简洁可学习的架构

**使用场景**:
- 嵌入式设备 AI 助手
- 边缘计算场景
- 教育和研究项目
- 低成本 AI 原型

**与同类项目差异**:
- **学术背景**: 由哈佛、MIT、Sundai.Club 学生构建
- **100% Rust**: 纯 Rust 实现
- **超轻量**: <5MB RAM（比 OpenClaw 少 99%）
- **低成本**: $10 硬件（比 Mac mini 便宜 98%）
- **多语言**: 支持 30+ 语言文档

## README 中文简介

**🦀 ZeroClaw** — 个人 AI 助手

**零开销。零妥协。100% Rust。100% Agnostic。**

**⚡️ 在 $10 硬件上运行仅需 <5MB RAM**：比 OpenClaw 少 99% 内存，比 Mac mini 便宜 98%！

**由哈佛、MIT 和 Sundai.Club 社区的学生和成员构建。**

**🌐 语言**:
🇺🇸 English · 🇨🇳 简体中文 · 🇯🇵 日本語 · 🇰🇷 한국어 · 🇻🇳 Tiếng Việt · 🇵🇭 Tagalog · 🇪🇸 Español · 🇧🇷 Português · 🇮🇹 Italiano · 🇩🇪 Deutsch · 🇫🇷 Français · 🇸🇦 العربية · 🇮🇳 हिन्दी · 🇷🇺 Русский · 🇧🇩 বাংলা · ...（共 30+ 语言）

**项目说明**:

ZeroClaw 是一个追求极致效率和可移植性的个人 AI 助手项目。它展示了如何在资源极其有限的环境下运行现代 AI 功能。

**核心特点**:
- **100% Rust**: 利用 Rust 的零成本抽象和内存安全
- **100% Agnostic**: 不绑定特定 AI 提供商或平台
- **零开销**: 无运行时垃圾回收，无虚拟机
- **零妥协**: 功能完整但资源占用极低

**社区**:
由哈佛、MIT 和 Sundai.Club 的活跃社区成员共同开发和维护。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 超轻量 | <5MB RAM | README | 高 |
| 低成本 | $10 硬件 | README | 高 |
| 100% Rust | Rust 实现 | README | 高 |
| 提供商无关 | 不绑定特定 AI | README | 高 |
| 多语言 | 30+ 语言支持 | README | 高 |
| 学术背景 | 哈佛/MIT/Sundai | README | 高 |
| 零开销 | 无 GC/VM | README | 高 |
| 边缘优化 | 嵌入式友好 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              ZeroClaw 架构                                   │
│           (零开销个人 AI 助手)                             │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              接口层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ CLI          │ Tauri UI     │ Web          ││  │
│  │   │ (命令行)     │ (桌面应用)   │ (Web UI)     ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ Python API   │ Firmware     │ Skills       ││  │
│  │   │ (Python)     │ (嵌入式)     │ (技能)       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心层 (Rust)                         │  │
│  │                                                  │  │
│  │   • Agent 运行时                                 │  │
│  │   • 工具系统                                     │  │
│  │   • 内存管理                                     │  │
│  │   • 异步处理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              提供商层                              │  │
│  │                                                  │  │
│  │   • OpenAI                                       │  │
│  │   • Anthropic                                    │  │
│  │   • 其他 LLM 提供商                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心 | `src/` | Rust 核心 | 核心 |
| 应用 | `apps/tauri/` | Tauri UI | 应用 |
| Python | `python/` | Python API | 接口 |
| 固件 | `firmware/` | 嵌入式固件 | 嵌入式 |
| 技能 | `skills/` | 技能定义 | 扩展 |
| 示例 | `examples/` | 示例代码 | 示例 |

## 运行与开发方式

**快速开始**:
```bash
# 克隆仓库
git clone https://github.com/theonlyhennygod/zeroclaw.git
cd zeroclaw

# 构建
cargo build --release

# 运行
./target/release/zeroclaw
```

**Tauri UI**:
```bash
cd apps/tauri
cargo tauri dev
```

**Python API**:
```bash
cd python
pip install -e .
```

**安装脚本**:
```bash
./install.sh
```

## 外部接口

**CLI**:
```bash
zeroclaw [command] [flags]
```

**Python API**:
```python
import zeroclaw

agent = zeroclaw.Agent()
response = agent.chat("Hello")
```

**Tauri/Web UI**:
桌面应用界面和 Web 界面

## 数据流 / 控制流

```
用户输入 (CLI/UI/API)
    ↓
Agent Core (Rust)
    ↓
工具调用
    ↓
LLM Provider
    ↓
响应生成
    ↓
返回用户
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Rust | 核心语言 | 高 |
| Tauri | 桌面 UI | 高 |
| Python | API 绑定 | 高 |
| Nix | 开发环境 | 中 |
| Docker | 容器化 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 30+ 语言 README | 高 |
| 上手难度 | 中 | 需要 Rust 环境 | 中 |
| 架构复杂度 | 中 | 多平台支持 | 中 |
| 外部依赖 | 低 | Rust 依赖 | 低 |
| Stars | 低 | 66 stars | 低 |
| 维护状态 | 中 | 学术项目 | 中 |

**注意事项**:
- 是 fork 项目（来自 zeroclaw-labs/zeroclaw）
- 学术项目，可能不够稳定
- 需要验证实际内存占用

**社区**:
- 哈佛
- MIT
- Sundai.Club

## 关联概念

- [[Rust]] - Rust 编程语言
- [[Tauri]] - 跨平台桌面应用框架
- [[Edge-AI]] - 边缘 AI
- [[Embedded-AI]] - 嵌入式 AI
- [[Harvard]] - 哈佛大学
- [[MIT]] - 麻省理工学院
- [[OpenClaw]] - 对比基准
- [[Zero-Cost-Abstraction]] - 零成本抽象

---

> 来源: [GitHub](https://github.com/theonlyhennygod/zeroclaw) | 置信度: 基于 GitHub README
> 👤 **作者**: theonlyhennygod (Harvard/MIT/Sundai.Club)
> ⭐ **Stars**: 66
> 🔗 **官网**: [GitHub](https://github.com/theonlyhennygod/zeroclaw)
> 📜 **许可证**: Apache-2.0 / MIT
