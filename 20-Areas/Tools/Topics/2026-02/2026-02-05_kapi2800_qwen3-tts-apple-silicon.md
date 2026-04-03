---
title: "kapi2800/qwen3-tts-apple-silicon: 本地 TTS (426 stars)"
github: "https://github.com/kapi2800/qwen3-tts-apple-silicon"
owner: kapi2800
repo: qwen3-tts-apple-silicon
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, tts, mlx, macos, apple-silicon, offline]
pinboard_tags: [tts, mlx, macos]
source_used: github-readme-extract
source_url: "https://github.com/kapi2800/qwen3-tts-apple-silicon"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# kapi2800/qwen3-tts-apple-silicon: Apple Silicon 本地 TTS

## 一句话概述

在 MacBook Apple Silicon (M1/M2/M3/M4) 上本地运行 Qwen3-TTS 文本转语音 AI，无需云、无需 API 密钥，完全离线，使用 Apple MLX 框架优化。

## 项目定位

**目标用户**:
- 需要在 Mac 上本地运行 TTS 的用户
- 关注隐私、不希望数据上云的用户
- 寻求 Apple Silicon 优化的开发者
- 需要语音克隆功能的创意工作者

**解决的问题**:
- **云端依赖**: 传统 TTS 需要联网和 API 密钥
- **隐私担忧**: 语音数据发送到云端处理
- **Apple Silicon 优化差**: 通用模型在 Mac 上性能不佳
- **资源消耗高**: 标准 PyTorch 模型 RAM 占用大、发热严重
- **网络延迟**: 云端 TTS 有网络延迟

**使用场景**:
- 本地语音合成和配音
- 语音克隆（5 秒样本克隆任意声音）
- 有声读物制作
- 无障碍辅助工具
- 隐私敏感场景

**与同类项目差异**:
- **100% 本地**: 完全离线，无网络依赖
- **MLX 优化**: 专为 Apple Silicon 优化
- **低资源占用**: 2-3 GB RAM vs 10+ GB
- **低温运行**: CPU 温度显著降低
- **GPU 推理**: 使用 Apple GPU 加速

## README 中文简介

**Qwen3-TTS for Mac** - 在 Apple Silicon 上本地运行 AI 文本转语音

**关键词**: Qwen TTS Mac, Qwen3 TTS Apple Silicon, MLX text to speech, local TTS Mac, voice cloning Mac, AI voice generator MacBook

**特性**:

**语音克隆**: 从 5 秒音频样本克隆任意声音

**声音设计**: 通过描述创建新声音（"深沉旁白"、"兴奋的儿童"）

**自定义声音**: 9 种内置声音，支持情感和速度控制

**100% 本地**: 完全在 Mac 上运行，无需互联网

**M 系列优化**: 使用 Apple MLX 框架进行快速 GPU 推理

**为什么用 MLX 模型?**

MLX 模型专为 Apple Silicon 优化。相比运行标准 PyTorch 模型：

| 指标 | 标准模型 | MLX 模型 |
|------|----------|----------|
| RAM 使用 | 10+ GB | 2-3 GB |
| CPU 温度 | 80-90°C | 显著更低 |

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 语音克隆 | 5 秒样本克隆任意声音 | README | 高 |
| 声音设计 | 描述创建新声音 | README | 高 |
| 内置声音 | 9 种声音 + 情感/速度控制 | README | 高 |
| 100% 本地 | 完全离线运行 | README | 高 |
| MLX 优化 | Apple Silicon GPU 推理 | README | 高 |
| 低 RAM | 2-3 GB vs 10+ GB | README | 高 |
| 低温运行 | CPU 温度显著降低 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Qwen3-TTS Mac 架构                              │
│           (Apple Silicon 本地 TTS)                         │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   • 文本输入                                     │  │
│  │   • 声音选择/克隆                                │  │
│  │   • 音频输出                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              MLX 优化层                            │  │
│  │                                                  │  │
│  │   • MLX 框架                                     │  │
│  │   • Apple GPU 加速                               │  │
│  │   • 内存优化                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              TTS 模型层                            │  │
│  │                                                  │  │
│  │   • Qwen3-TTS 模型                               │  │
│  │   • 语音编码器                                   │  │
│  │   • 声学模型                                     │  │
│  │   • 声码器                                       │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 主程序 | `main.py` | 入口和流程控制 | 核心 |
| 声音 | `voices/` | 内置声音资源 | 资源 |
| 输出 | `outputs/` | 生成的音频 | 输出 |

## 运行与开发方式

**安装**:
```bash
# 克隆仓库
git clone https://github.com/kapi2800/qwen3-tts-apple-silicon.git
cd qwen3-tts-apple-silicon

# 安装依赖
pip install -r requirements.txt
```

**运行**:
```bash
python main.py
```

**开发**:
```bash
# 需要 Apple Silicon Mac
# MLX 框架自动使用 GPU
```

## 外部接口

**CLI 使用**:
```bash
python main.py --text "Hello world" --voice default
```

**Python API**:
```python
from main import TTS

tts = TTS()
audio = tts.synthesize("Hello world", voice="default")
```

## 数据流 / 控制流

```
文本输入
    ↓
MLX 预处理
    ↓
Qwen3-TTS 模型 (Apple GPU)
    ↓
音频生成
    ↓
输出播放/保存
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| MLX | Apple ML 框架 | 高 |
| PyTorch | 基础 (MLX 兼容) | 中 |
| Apple Silicon | 目标平台 | 高 |
| Qwen3 | TTS 模型 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 简洁 | 中 |
| 上手难度 | 低 | pip 安装即可 | 低 |
| 架构复杂度 | 低 | 封装 MLX 模型 | 低 |
| 外部依赖 | 低 | 完全本地 | 低 |
| Stars | 低 | 426 stars | 低 |
| 维护状态 | 中 | 新项目 (3 commits) | 中 |

**注意事项**:
- 仅支持 Apple Silicon Mac
- 需要 MLX 框架支持
- 项目较新，功能可能有限
- 中文语音支持需验证

**硬件要求**:
- Apple Silicon (M1/M2/M3/M4)
- 2-3 GB 可用 RAM
- macOS (支持 MLX)

## 关联概念

- [[Qwen3]] - 阿里巴巴 Qwen3 模型
- [[MLX]] - Apple Machine Learning framework
- [[TTS]] - Text-to-Speech 语音合成
- [[Voice-Cloning]] - 语音克隆技术
- [[Apple-Silicon]] - Apple M 系列芯片
- [[Offline-AI]] - 本地离线 AI

---

> 来源: [GitHub](https://github.com/kapi2800/qwen3-tts-apple-silicon) | 置信度: 基于 GitHub README
> 👤 **作者**: kapi2800
> ⭐ **Stars**: 426
> 🔗 **官网**: [GitHub](https://github.com/kapi2800/qwen3-tts-apple-silicon)
> 📜 **许可证**: 未明确
