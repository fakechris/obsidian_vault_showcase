---
title: "OpenBMB/MiniCPM-o: 端侧多模态大模型 (24.3k stars)"
github: "https://github.com/OpenBMB/MiniCPM-o"
owner: OpenBMB
repo: MiniCPM-o
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, multimodal-llm, vision, speech, on-device, pytorch, llama.cpp]
pinboard_tags: [ai-model, multimodal, vision, speech]
source_used: github-readme-extract
source_url: "https://github.com/OpenBMB/MiniCPM-o"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# OpenBMB/MiniCPM-o: 端侧多模态大模型

## 一句话概述

MiniCPM-o 是一个可在手机端部署的多模态大模型系列，支持图像、视频、文本、音频输入和文本/语音输出，最新 4.5 版本以 9B 参数达到 Gemini 2.5 Flash 级别性能，支持全双工实时音视频对话，是开源社区最强大的端侧多模态模型之一。

## 项目定位

**目标用户**:
- 需要在端侧部署多模态 AI 的开发者和研究者
- 构建手机 AI 应用、智能助手的产品团队
- 关注隐私、希望本地运行 AI 的用户
- 多模态 AI 研究人员

**解决的问题**:
- **云端依赖**: 主流多模态模型依赖云端 API，存在延迟和隐私问题
- **端侧性能**: 大模型难以在手机等资源受限设备上运行
- **多模态整合**: 视觉、语音、文本需要分别调用不同模型
- **实时交互**: 缺乏支持实时音视频流的多模态模型
- **中文支持**: 很多开源模型中文能力较弱

**使用场景**:
- 手机端智能助手(拍照识图、语音对话)
- 实时视频理解与描述
- 端到端语音交互应用
- 本地隐私敏感场景
- 多模态内容创作

**与同类项目差异**:
- **端侧优化**: 专为手机等设备优化，MiniCPM-V 4.0 仅需 4B 参数
- **全模态支持**: 图像、视频、文本、音频统一处理
- **全双工对话**: MiniCPM-o 4.5 支持实时音视频同时输入输出
- **中文优化**: 针对中文场景优化，支持双语实时语音对话
- **开源可商用**: Apache-2.0 许可证，可商用

## README 中文简介

**MiniCPM-o** - 手机端 Gemini 2.5 Flash 级别多模态大模型

MiniCPM-o 是 MiniCPM-V 系列的最新端侧多模态 LLM，支持图像、视频、文本、音频输入，提供高质量文本和语音输出。

**核心模型**:

**MiniCPM-o 4.5** (最新最强):
- **9B 参数**，端到端架构
- **接近 Gemini 2.5 Flash** 的视觉、语音和全双工多模态实时流媒体能力
- **全双工多模态实时流媒体**: 可以同时看到、听到、说话，输出流(语音和文本)与实时输入流(视频和音频)互不阻塞
- **主动交互**: 能主动发起提醒或评论
- **语音克隆**: 支持通过参考音频克隆声音，效果超越 CosyVoice2 等 TTS 工具
- **OCR**: 端到端英文文档解析在 OmniDocBench 达到 SOTA

**MiniCPM-V 4.0** (高效版本):
- **4B 参数**，图像理解超越 GPT-4.1-mini
- 专为端侧部署设计
- iPhone 16 Pro Max 首 token 延迟 <2s，解码速度 >17 token/s

**技术架构**:

**端到端全模态架构**:
- 模态编码器/解码器与 LLM 通过隐藏状态密集连接
- 支持更好的信息流动和控制

**全双工全模态实时流媒体机制**:
- 将离线模态编码器/解码器转换为在线全双工版本
- 语音 token 解码器以交错方式建模文本和语音 token
- 时间分复用(TDM)机制处理并行全模态流

**主动交互机制**:
- LLM 以 1Hz 频率持续监控输入流，决定是否说话

**评估结果**:

**图像理解 (Instruct)**:
- MiniCPM-o 4.5: OpenCompass **77.6**，超越 GPT-4o、Gemini 2.0 Pro，接近 Gemini 2.5 Flash (78.5)

**文档解析 (OmniDocBench)**:
- MiniCPM-o 4.5 英文文档解析达到 SOTA，超越 Gemini-3 Flash、GPT-5、DeepSeek-OCR 2

**视频理解**:
- Video-MME: MiniCPM-o 4.5 70.4 (接近 Gemini 2.5 Flash 75.6)

**语音生成**:
- SeedTTS 测试集 CER: MiniCPM-o 4.5 **0.86%** (优于 CosyVoice2 1.45%、Qwen3-Omni 1.41%)

**推理效率**:
- MiniCPM-o 4.5 bf16: 154.3 tokens/s，首 token 0.6s，显存 19GB
- MiniCPM-o 4.5 int4: 212.3 tokens/s，首 token 0.6s，显存 11GB

**使用方式**:

**Transformers (推荐)**:
```python
import torch
from transformers import AutoModel

model = AutoModel.from_pretrained(
    "openbmb/MiniCPM-o-4_5",
    trust_remote_code=True,
    attn_implementation="sdpa",
    torch_dtype=torch.bfloat16,
    init_vision=True,
    init_audio=True,
    init_tts=True,
)
model.eval().cuda()
model.init_tts()
```

**llama.cpp / Ollama**: 支持 CPU 端侧高效推理
**vLLM / SGLang**: 高吞吐量服务部署
**iOS App**: 已开源 iPhone/iPad 应用

**框架支持**:
- FlagOS: 支持多芯片后端(Nvidia、海光、摩尔线程、天数智芯、华为昇腾)
- llama.cpp-omni: 本地实时全双工体验

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 图像理解 | 单图/多图理解，超越 GPT-4V | README | 高 |
| 视频理解 | 实时视频流理解 | README | 高 |
| 语音识别 | ASR 和多语言语音理解 | README | 高 |
| 语音合成 | TTS 和零样本语音克隆 | README | 高 |
| 全双工对话 | 实时音视频同时输入输出 | README | 高 |
| 主动交互 | 能主动发起提醒/评论 | README | 高 |
| OCR 文档解析 | 端到端文档理解 SOTA | README | 高 |
| 端侧部署 | 支持手机本地运行 | README | 高 |
| 多框架支持 | Transformers/llama.cpp/vLLM/SGLang | README | 高 |
| 多芯片支持 | Nvidia/海光/摩尔线程/昇腾等 | README | 高 |
| 双语支持 | 中英文实时语音对话 | README | 高 |
| iOS 应用 | 已开源 iPhone/iPad App | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              MiniCPM-o 架构                                │
│           (端侧多模态大模型)                               │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              模态编码器层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ SigLip2      │ Whisper      │ 视频编码     ││  │
│  │   │ (视觉)       │ (音频)       │              ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              LLM 骨干网络 (Qwen3-8B)               │  │
│  │                                                  │  │
│  │   • 隐藏状态密集连接编码器/解码器                │  │
│  │   • 时间分复用(TDM)处理并行流                    │  │
│  │   • 全双工语音 token 交错建模                    │  │
│  │   • 主动交互决策(1Hz)                            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              模态解码器层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ 文本生成     │ CosyVoice2   │              │  │
│  │   │              │ (语音合成)   │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              部署运行时                              │  │
│  │                                                  │  │
│  │   ┌────────┬────────┬────────┬────────┐       │  │
│  │   │PyTorch │llama. │ vLLM   │ SGLang │       │  │
│  │   │(GPU)   │cpp    │(服务)  │(服务)  │       │  │
│  │   ├────────┼────────┼────────┼────────┤       │  │
│  │   │FlagOS  │Ollama  │iOS App │WebRTC │       │  │
│  │   │(多芯片)│(本地)  │(端侧)  │(实时) │       │  │
│  │   └────────┴────────┴────────┴────────┘       │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 模型权重 | HuggingFace | 预训练权重 | 核心 |
| 推理代码 | `omnilmm/` | 模型推理实现 | 核心 |
| 微调训练 | `finetune/` | LoRA/SFT 微调 | 扩展 |
| Web Demo | `web_demos/` | 实时交互演示 | 示例 |
| 评估 | `eval_mm/` | 多模态评估 | 质量 |
| iOS App | 独立仓库 | 端侧应用 | 产品 |

## 运行与开发方式

**环境要求**:
- Python 3.10+
- PyTorch 2.3-2.8
- transformers==4.51.0
- CUDA GPU (推荐) 或 Apple Silicon

**快速开始**:
```bash
# 安装依赖
pip install "transformers==4.51.0" accelerate \
  "torch>=2.3.0,<=2.8.0" "torchaudio<=2.8.0" \
  "minicpmo-utils[all]>=1.0.5"

# 可选: FFmpeg 视频处理
brew install ffmpeg  # macOS
```

**模型加载**:
```python
import torch
from transformers import AutoModel

model = AutoModel.from_pretrained(
    "openbmb/MiniCPM-o-4_5",
    trust_remote_code=True,
    attn_implementation="sdpa",  # 或 flash_attention_2
    torch_dtype=torch.bfloat16,
    init_vision=True,
    init_audio=True,
    init_tts=True,
)
model.eval().cuda()
model.init_tts()
```

**单图对话**:
```python
from PIL import Image

image = Image.open("image.jpg").convert("RGB")
question = "描述这张图片"
msgs = [{"role": "user", "content": [image, question]}]
res = model.chat(msgs=msgs, use_tts_template=False)
print(res)
```

**实时语音对话**:
```python
import librosa

# 加载参考音频进行语音克隆
ref_audio, _ = librosa.load("ref_voice.wav", sr=16000, mono=True)

sys_msg = {
    "role": "system",
    "content": [
        "克隆提供音频中的声音。",
        ref_audio,
        "你是由面壁智能开发的 AI 助手：面壁小钢炮。"
    ]
}

# 流式生成语音回复
model.streaming_prefill(session_id="demo", msgs=[sys_msg])
# ... 流式处理音频输入
```

**本地 Web 部署**:
```bash
# 需要 28GB+ GPU 显存
# 支持全双工实时音视频对话
# 提供 WebRTC Demo
```

**llama.cpp-omni (Mac/低资源设备)**:
```bash
# 半双工语音对话: Apple M3/M4 16GB RAM 或 12GB GPU
# 全双工多模态: Apple M4 Max 24GB RAM 或 12GB GPU
# Docker 镜像一键部署
```

## 外部接口

**Python API**:
| 方法 | 功能 |
|------|------|
| `model.chat()` | 标准对话(图文/音视频) |
| `model.streaming_prefill()` | 流式预填充 |
| `model.streaming_generate()` | 流式生成 |
| `model.as_duplex()` | 切换到全双工模式 |
| `model.init_tts()` | 初始化语音合成 |
| `model.reset_session()` | 重置会话状态 |

**OpenAI 兼容格式**:
```python
msgs = [
    {"role": "user", "content": [
        {"type": "image_url", "image_url": {"url": "/path/to/image.jpg"}},
        {"type": "text", "text": "描述这张图片"}
    ]}
]
```

**服务部署**:
| 方式 | 适用场景 | 显存需求 |
|------|----------|----------|
| PyTorch | 100% 精度本地开发 | 19GB (bf16) / 11GB (int4) |
| llama.cpp | CPU/端侧推理 | 10GB (gguf) |
| vLLM | 高吞吐服务 | 兼容 FlagOS 多芯片 |
| SGLang | 高性能服务 | 多模态流式支持 |
| iOS App | 手机端侧 | 4GB |

## 数据流 / 控制流

```
用户输入 (图像/音频/文本)
    ↓
模态编码器 (SigLip2/Whisper)
    ↓
隐藏状态 → LLM (Qwen3-8B)
    ↓
┌────────────────────────────────┐
│ 全双工模式?                    │
└────────────────────────────────┘
    ↓ 是                  ↓ 否
实时流处理            标准生成
TDM 时间分复用         ↓
交错语音 token        文本/语音输出
    ↓
模态解码器
    ↓
输出 (文本 + 语音)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (83.2%) | 高 |
| PyTorch | 深度学习框架 | 高 |
| Transformers | HuggingFace 库 | 高 |
| Qwen3-8B | LLM 骨干网络 | 高 |
| SigLip2 | 视觉编码器 | 高 |
| Whisper | 音频编码器 | 高 |
| CosyVoice2 | 语音解码器 | 高 |
| llama.cpp | 端侧推理 | 高 |
| Vue | Web Demo (14.1%) | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细 README、技术报告、Cookbook | 高 |
| 上手难度 | 中 | 需要 GPU 和特定依赖版本 | 中 |
| 架构复杂度 | 高 | 端到端多模态架构 | 高 |
| 外部依赖 | 中 | 依赖特定 transformers 版本 | 中 |
| Stars | 高 | 24.3k stars | 高 |
| 社区活跃度 | 高 | 活跃开发，多框架支持 | 高 |

**注意事项**:
- 需要 transformers==4.51.0，其他版本可能不兼容
- 实时 Web Demo 需要 28GB+ GPU 显存
- llama.cpp/Ollama 分支等待合并到官方仓库期间需使用项目 fork
- 生产部署建议使用官方推荐的 FlagOS 多芯片版本

## 关联概念

- [[Multimodal-LLM]] - 多模态大模型
- [[Vision-Language-Model]] - 视觉语言模型
- [[Speech-Synthesis]] - 语音合成
- [[On-Device-AI]] - 端侧 AI
- [[Full-Duplex-Conversation]] - 全双工对话
- [[llama.cpp]] - 大模型本地推理框架
- [[Qwen]] - 阿里云通义千问模型
- [[OpenBMB]] - 面壁智能

---

> 来源: [GitHub](https://github.com/OpenBMB/MiniCPM-o) | 置信度: 基于 GitHub README
> 👤 **作者**: OpenBMB (面壁智能) + THUNLP (清华 NLP 实验室)
> ⭐ **Stars**: 24.3k
> 🔗 **官网**: [MiniCPM 文档](https://minicpm.gitbook.io/minicpm)
> 📜 **许可证**: Apache-2.0
