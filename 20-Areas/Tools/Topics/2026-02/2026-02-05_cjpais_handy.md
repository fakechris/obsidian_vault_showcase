---
title: "cjpais/Handy: 开源离线语音转文字应用 (19.1k stars)"
github: "https://github.com/cjpais/Handy"
owner: cjpais
repo: Handy
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, speech-to-text, whisper, offline, privacy, tauri, rust]
pinboard_tags: [speech-to-text, privacy, whisper]
source_used: github-readme-extract
source_url: "https://github.com/cjpais/Handy"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# cjpais/Handy: 开源离线语音转文字应用

## 一句话概述

Handy 是一个免费、开源、可扩展的跨平台语音转文字应用，完全离线运行，通过快捷键触发录音，使用 Whisper 模型在本地完成语音识别，保护用户隐私的同时提供高效的语音输入体验。

## 项目定位

**目标用户**:
- 需要语音输入功能的用户
- 关注隐私、不希望数据上云的用户
- 开源软件爱好者和贡献者
- 需要可扩展语音工具的开发者和团队

**解决的问题**:
- **商业软件付费墙**: 主流语音工具通常需要付费订阅
- **隐私泄露风险**: 云端语音识别服务会传输用户音频数据
- **开源替代品缺失**: 缺乏真正开源、可扩展的语音转文字工具
- **跨平台不一致**: 不同平台需要不同的语音输入方案

**使用场景**:
- 快速语音输入转文字到任何应用
- 会议记录和笔记整理
- 程序员代码注释语音输入
- 无障碍辅助工具

**与同类项目差异**:
- **完全开源**: 代码完全开放，可自由 fork 和定制
- **本地运行**: 所有处理在本地完成，音频不上传云端
- **Whisper 引擎**: 使用 OpenAI Whisper 模型，支持多语言
- **Tauri 架构**: Rust + React 构建，性能优秀跨平台
- **Raycast 集成**: 提供 Raycast 扩展，增强工作流

## README 中文简介

**Handy** - 免费开源、可扩展的离线语音转文字应用

**核心特点**:
- **免费**: 无障碍工具应该人人可用，而非付费墙后
- **开源**: 共同构建、自由扩展、为更大生态贡献
- **隐私**: 语音留在你的电脑上，无需发送到云端
- **简单**: 一个工具一个职责，语音识别并输入到文本框

**工作原理**:
1. 按下可配置的快捷键开始/停止录音(或按住说话模式)
2. 说话时保持快捷键激活
3. 释放快捷键，Handy 使用 Whisper 处理语音
4. 转录文字直接粘贴到你使用的任何应用中

**技术栈**:
- **前端**: React + TypeScript + Tailwind CSS
- **后端**: Rust (Tauri)
- **语音识别**: whisper-rs (Whisper 模型) / transcription-rs (Parakeet V3)
- **音频处理**: cpal (跨平台音频 I/O) / vad-rs (语音活动检测)
- **快捷键**: rdev (全局快捷键和系统事件)

**支持的模型**:
- Whisper Small/Medium/Turbo/Large (支持 GPU 加速)
- Parakeet V3 (CPU 优化模型，自动语言检测)

**安装方式**:
```bash
# macOS (Homebrew)
brew install --cask handy

# Windows (winget)
winget install cjpais.Handy

# 或直接下载 release
```

**CLI 参数**:
```bash
handy --toggle-transcription    # 切换录音
handy --toggle-post-process     # 切换录音并后处理
handy --cancel                  # 取消当前操作
handy --start-hidden            # 启动时隐藏主窗口
handy --debug                   # 启用调试模式
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 离线语音识别 | 使用 Whisper 本地模型 | README | 高 |
| 跨平台支持 | Windows, macOS, Linux | README | 高 |
| 快捷键触发 | 可配置的全局快捷键 | README | 高 |
| 按住说话模式 | 支持 push-to-talk | README | 高 |
| VAD 静音过滤 | Silero 语音活动检测 | README | 高 |
| GPU 加速 | Whisper 模型支持 CUDA | README | 高 |
| Raycast 集成 | 控制录音、浏览历史 | README | 高 |
| 调试模式 | Cmd/Ctrl+Shift+D 进入 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Handy 架构                                    │
│           (离线语音转文字应用)                              │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              前端层 (React + TS)                  │  │
│  │                                                  │  │
│  │   • 设置 UI (Tailwind CSS)                       │  │
│  │   • 快捷键配置                                   │  │
│  │   • 模型选择                                     │  │
│  │   • 录音状态显示                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Tauri 层 (Rust)                      │  │
│  │                                                  │  │
│  │   • 系统集成                                     │  │
│  │   • 音频处理                                     │  │
│  │   • ML 推理                                      │  │
│  │   • 全局快捷键                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              语音识别引擎                          │  │
│  │                                                  │  │
│  │   ┌──────────────┐ ┌──────────────┐              │  │
│  │   │ Whisper 模型 │ │ Parakeet V3  │              │  │
│  │   │              │ │              │              │  │
│  │   │ • Small      │ │ • CPU 优化   │              │  │
│  │   │ • Medium     │ │ • 自动语言   │              │  │
│  │   │ • Turbo      │ │   检测       │              │  │
│  │   │ • Large      │ │              │              │  │
│  │   └──────────────┘ └──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              音频处理层                            │  │
│  │                                                  │  │
│  │   • cpal - 跨平台音频 I/O                        │  │
│  │   • vad-rs - 语音活动检测                        │  │
│  │   • rubato - 音频重采样                          │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 前端 UI | src/ | React 设置界面 | 用户接口 |
| Tauri 后端 | src-tauri/ | Rust 系统集成 | 核心引擎 |
| 音频处理 | vad-rs, cpal | 录音和 VAD | 依赖库 |
| 语音识别 | whisper-rs | Whisper 模型推理 | 依赖库 |
| Raycast 扩展 | 外部 | 工作流集成 | 扩展 |

## 运行与开发方式

**开发环境**:
```bash
# 克隆仓库
git clone https://github.com/cjpais/Handy.git
cd Handy

# 安装依赖
bun install

# 开发模式
bun dev

# 构建
bun run build
```

**详细构建说明**: 参见 BUILD.md

**使用方式**:
1. 安装并启动 Handy
2. 授予系统权限(麦克风、辅助功能)
3. 配置快捷键
4. 按快捷键开始录音
5. 说话后释放，文字自动粘贴

**调试模式**:
- macOS: Cmd+Shift+D
- Windows/Linux: Ctrl+Shift+D

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `--toggle-transcription` | 切换录音状态 |
| `--toggle-post-process` | 切换录音并后处理 |
| `--cancel` | 取消当前操作 |
| `--start-hidden` | 隐藏启动 |
| `--no-tray` | 不显示托盘图标 |
| `--debug` | 调试模式 |

**快捷键**:
- 可配置的全局快捷键
- 支持按住说话模式
- 支持切换模式

**集成**:
- Raycast 扩展: 控制、历史、词典管理

## 数据流 / 控制流

```
用户按下快捷键
    ↓
开始录音 (cpal)
    ↓
VAD 检测语音活动
    ↓
用户释放快捷键
    ↓
音频发送到 Whisper/Parakeet
    ↓
本地推理生成文字
    ↓
文字粘贴到当前应用
    ↓
完成
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| React + TypeScript | 前端 | 高 |
| Tailwind CSS | UI | 高 |
| Rust (Tauri) | 后端 | 高 |
| Whisper | 语音识别 | 高 |
| cpal | 音频 I/O | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README + BUILD.md | 高 |
| 上手难度 | 低 | 安装即用 | 低 |
| 架构复杂度 | 中 | Tauri + ML | 中 |
| 外部依赖 | 低 | 完全离线 | 低 |
| Stars | 高 | 19.1k stars | 高 |
| 活跃状态 | 高 | 活跃开发 | 高 |

**注意事项**:
- Whisper 模型在某些配置下可能崩溃
- Wayland 支持有限(需要 wtype/dotool)
- Linux 需要额外安装 xdotool/wtype

## 关联概念

- [[Whisper]] - OpenAI 语音识别模型
- [[Tauri]] - Rust + Web 跨平台框架
- [[Speech-to-Text]] - 语音转文字技术
- [[VAD]] - 语音活动检测
- [[Privacy-First]] - 隐私优先设计

---

> 来源: [GitHub](https://github.com/cjpais/Handy) | 置信度: 基于 GitHub README
> 👤 **作者**: cjpais
> ⭐ **Stars**: 19.1k
> 🔗 **官网**: handy.computer
> 📜 **许可证**: MIT
