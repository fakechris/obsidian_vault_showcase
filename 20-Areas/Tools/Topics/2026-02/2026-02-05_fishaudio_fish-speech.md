---
title: "fishaudio/fish-speech: 开源 TTS 文本转语音 (29k stars)"
github: "https://github.com/fishaudio/fish-speech"
owner: fishaudio
repo: fish-speech
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, tts, text-to-speech, speech-synthesis, multilingual, python, llm]
pinboard_tags: [ai-model, speech, tts]
source_used: github-readme-extract
source_url: "https://github.com/fishaudio/fish-speech"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# fishaudio/fish-speech: 开源 TTS 文本转语音

## 一句话概述

Fish Speech 是一个 SOTA 开源多语言文本转语音(TTS)系统，S2 Pro 版本采用 4B 参数 Dual-AR 架构和强化学习对齐，支持 80+ 语言、15,000+ 自然语言控制标签（情感/语调/停顿），实现零样本语音克隆和极低延迟(100ms TTFA)的实时语音合成。

## 项目定位

**目标用户**:
- 需要高质量语音合成解决方案的开发者和企业
- 构建 AI 助手、有声读物、配音系统的团队
- 研究多模态语音技术的研究人员
- 需要私有化部署 TTS 的用户

**解决的问题**:
- **TTS 质量**: 开源 TTS 与商业方案存在质量差距
- **多语言支持**: 多数 TTS 仅支持少数主流语言
- **情感控制**: 难以通过自然方式控制语音情感语调
- **实时性**: 生产环境需要低延迟语音合成
- **语音克隆**: 需要高质量少样本语音克隆

**使用场景**:
- AI 助手和聊天机器人语音
- 有声读物和播客制作
- 游戏和动画配音
- 实时语音翻译
- 个性化语音克隆

**与同类项目差异**:
- **SOTA 性能**: Seed-TTS Eval 最低 WER(0.54% 中文/0.99% 英文)
- **15,000+ 标签**: 支持丰富的自然语言情感/语调控制
- **Dual-AR 架构**: 4B 慢 AR + 400M 快 AR 实现高质量+高效率
- **强化学习对齐**: GRPO 优化确保语义准确和声学质量
- **SGLang 加速**: 支持 Continuous Batching、Paged KV Cache，RTF 0.195

## README 中文简介

**Fish Speech** - 最先进的开源多语言 TTS 系统

**Fish Audio S2 Pro**:
- **40 亿参数** Dual-AR 架构多模态模型
- **超过 1000 万小时**音频数据训练，覆盖 80+ 语言
- **强化学习对齐**(GRPO)确保语音自然、真实、情感丰富
- **子词级细粒度控制**: 使用自然语言标签控制韵律和情感

**模型架构**:

**Dual-Autoregressive (Dual-AR) 架构**:
- **慢 AR (4B 参数)**: 沿时间轴运行，预测主语义码本
- **快 AR (400M 参数)**: 每个时间步生成剩余 9 个残差码本，重建精细声学细节
- **RVQ 音频编解码器**: 10 个码本，~21 Hz

**强化学习对齐**:
- 使用 Group Relative Policy Optimization (GRPO) 进行后训练对齐
- 直接使用模型套件作为奖励模型，解决预训练数据与后训练目标的分布不匹配
- 多维度奖励信号: 语义准确性、指令遵循、声学偏好评分、音色相似度

**基准测试结果**:

| 基准测试 | 结果 |
|----------|------|
| Seed-TTS Eval WER (中文) | **0.54%** (最佳) |
| Seed-TTS Eval WER (英文) | **0.99%** (最佳) |
| Audio Turing Test | **0.515** 后验均值 |
| EmergentTTS-Eval 胜率 | **81.88%** (最高) |
| Fish Instruction TAR | **93.3%** |
| Fish Instruction 质量 | **4.51/5.0** |

**多语言支持**:
- **Tier 1**: 日语、英语、中文
- **Tier 2**: 韩语、西班牙语、葡萄牙语、阿拉伯语、俄语、法语、德语
- **全球覆盖**: 80+ 语言，无需音素或语言特定预处理

**自然语言标签控制**:
```
[whisper] [small voice] [professional broadcast tone] [pitch up]
[laughing] [excited] [angry] [singing] [volume up]
[pause] [emphasis] [inhale] [chuckle] [sigh]
[audience laughter] [with strong accent] [clearing throat]
```

**极端流式性能 (SGLang)**:
- **RTF**: 0.195 (单 H200 GPU)
- **首音频时间**: ~100 ms
- **吞吐**: 3,000+ 声学 tokens/s，保持 RTF < 0.5

**快速开始**:

**安装**:
```bash
pip install fish-speech
# 或
uv add fish-speech
```

**命令行推理**:
```bash
python -m fish_speech generate "你好，这是测试"
```

**WebUI**:
```bash
python -m fish_speech webui
```

**API 服务**:
```bash
python -m fish_speech server
```

**SGLang-Omni (生产级)**:
请参考 SGLang-Omni README 获取高性能服务部署指南。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 多语言 TTS | 80+ 语言支持，无需音素 | README | 高 |
| 零样本语音克隆 | 10-30 秒参考音频克隆声音 | README | 高 |
| 自然语言控制 | 15,000+ 情感/语调标签 | README | 高 |
| Dual-AR 架构 | 4B 慢 AR + 400M 快 AR | README | 高 |
| 强化学习对齐 | GRPO 优化语义和声学 | README | 高 |
| 极低延迟 | TTFA ~100ms，RTF 0.195 | README | 高 |
| 多说话人 | 单次参考音频包含多说话人 | README | 高 |
| 多轮对话 | 利用上下文改进表达 | README | 高 |
| SGLang 加速 | Continuous Batching, Paged KV Cache | README | 高 |
| Docker 支持 | 提供容器化部署方案 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Fish Speech S2 Pro 架构                       │
│           (4B Dual-AR 多语言 TTS 系统)                       │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              文本输入层                            │  │
│  │                                                  │  │
│  │   输入: 文本 + 自然语言标签                      │  │
│  │   示例: "你好 [excited] 世界 [laughing]"           │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Dual-AR 架构层                        │  │
│  │                                                  │  │
│  │   ┌─────────────────────────────────────────┐  │  │
│  │   │           慢 AR (4B 参数)                   │  │  │
│  │   │  • 沿时间轴运行                            │  │  │
│  │   │  • 预测主语义码本                          │  │  │
│  │   │  • Decoder-only Transformer                │  │  │
│  │   └─────────────────────────────────────────┘  │  │
│  │                          │                     │  │
│  │                          ▼                     │  │
│  │   ┌─────────────────────────────────────────┐  │  │
│  │   │           快 AR (400M 参数)              │  │  │
│  │   │  • 每个时间步生成 9 个残差码本           │  │  │
│  │   │  • 重建精细声学细节                      │  │  │
│  │   └─────────────────────────────────────────┘  │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              RVQ 编解码器层                        │  │
│  │                                                  │  │
│  │   • 10 个码本，~21 Hz                           │  │
│  │   • 矢量量化音频表示                             │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              音频输出层                            │  │
│  │                                                  │  │
│  │   输出: 高质量语音波形                           │  │
│  │   支持: 多说话人、多轮对话                       │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              训练后对齐 (RL)                       │  │
│  │                                                  │  │
│  │   GRPO (Group Relative Policy Optimization)      │  │
│  │   ├── 语义准确性奖励                             │  │
│  │   ├── 指令遵循奖励                               │  │
│  │   ├── 声学偏好评分                               │  │
│  │   └── 音色相似度                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心推理 | `fish_speech/` | TTS 生成引擎 | 核心 |
| WebUI | `awesome_webui/` | 可视化界面 | 用户接口 |
| Docker | `docker/` | 容器化部署 | 部署 |
| 工具 | `tools/` | 辅助工具(量化等) | 扩展 |
| 配置 | `compose*.yml` | Docker Compose 配置 | 配置 |

## 运行与开发方式

**快速开始**:

**pip 安装**:
```bash
pip install fish-speech
```

**uv 安装**:
```bash
uv add fish-speech
```

**Docker**:
```bash
docker compose up
```

**命令行推理**:
```bash
python -m fish_speech generate "要合成的文本"
```

**启动 WebUI**:
```bash
python -m fish_speech webui
```

**启动 API 服务**:
```bash
python -m fish_speech server
```

**SGLang-Omni 高性能服务**:
```bash
# 参考 SGLang-Omni README 获取详细指南
# 支持 Continuous Batching, Paged KV Cache, CUDA Graph
```

**语音克隆**:
```python
from fish_speech import FishSpeech

model = FishSpeech()
# 10-30 秒参考音频
model.clone_voice("reference.wav")
model.generate("你好，这是克隆的声音")
```

## 外部接口

**Python API**:
| 方法 | 功能 |
|------|------|
| `generate(text)` | 合成语音 |
| `clone_voice(audio)` | 克隆声音 |
| `generate_with_speaker(text, speaker_id)` | 多说话人合成 |

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `fish_speech generate` | 文本转语音 |
| `fish_speech webui` | 启动 Web 界面 |
| `fish_speech server` | 启动 API 服务 |

**HTTP API**:
```python
# 服务启动后访问
POST /generate
{
  "text": "你好",
  "speaker_id": "default",
  "emotion_tags": ["excited"]
}
```

**模型变体**:
| 模型 | 大小 | 可用性 | 说明 |
|------|------|--------|------|
| S2-Pro | 4B 参数 | HuggingFace | 全功能旗舰版 |

## 数据流 / 控制流

```
文本输入 + 自然语言标签
    ↓
┌─────────────────────────────┐
│ 慢 AR (4B)                  │
│ • 沿时间轴生成语义码本     │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 快 AR (400M)                 │
│ • 生成 9 个残差码本          │
│ • 重建声学细节               │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ RVQ 解码器                   │
│ • 10 码本 → 音频波形         │
└──────────────┬──────────────┘
               ↓
           语音输出
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (80.8%) | 高 |
| TypeScript | WebUI (14.3%) | 高 |
| PyTorch | 深度学习框架 | 高 |
| Docker | 容器化 (3.0%) | 高 |
| SGLang | 推理加速 | 高 |
| RVQ | 矢量量化编解码 | 高 |
| Dual-AR | 自回归架构 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 官方文档、技术报告、多语言支持 | 高 |
| 上手难度 | 低 | pip/uv/Docker 一键安装 | 低 |
| 架构复杂度 | 高 | Dual-AR + RL 对齐 + RVQ | 高 |
| 外部依赖 | 中 | 依赖 SGLang 进行高性能推理 | 中 |
| Stars | 高 | 29k stars | 高 |
| 维护状态 | 高 | 活跃开发，14 个 releases | 高 |

**许可证警告**:
- 代码和模型权重使用 **FISH AUDIO RESEARCH LICENSE**
- 非商业研究可免费使用
- 商业使用需联系 Fish Audio
- 违反许可将面临法律行动

**注意事项**:
- 4B 模型需要较大显存
- 生产环境建议使用 SGLang-Omni
- 遵守许可证条款使用
- 语音克隆需注意伦理和法律问题

## 关联概念

- [[TTS]] - Text-to-Speech 文本转语音
- [[Dual-AR]] - Dual-Autoregressive 双自回归架构
- [[RVQ]] - Residual Vector Quantization 残差矢量量化
- [[GRPO]] - Group Relative Policy Optimization
- [[Voice-Cloning]] - 语音克隆技术
- [[SGLang]] - 大模型服务框架
- [[Multilingual-TTS]] - 多语言语音合成

---

> 来源: [GitHub](https://github.com/fishaudio/fish-speech) | 置信度: 基于 GitHub README
> 👤 **作者**: Fish Audio (Shijia Liao, Yuxuan Wang, etc.)
> ⭐ **Stars**: 29k
> 🔗 **官网**: [speech.fish.audio](https://speech.fish.audio)
> 📜 **许可证**: FISH AUDIO RESEARCH LICENSE
