---
title: "jsattler/BetterCapture: macOS 录屏工具 (1.1k stars)"
github: "https://github.com/jsattler/BetterCapture"
owner: jsattler
repo: BetterCapture
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, macos, screen-recorder, swift, opensource]
pinboard_tags: [macos, screen-recorder, swift]
source_used: github-readme-extract
source_url: "https://github.com/jsattler/BetterCapture"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# jsattler/BetterCapture: macOS 录屏工具

## 一句话概述

BetterCapture 是一个为 macOS 设计的屏幕录制工具，永远免费开源，原生 SwiftUI 开发，基于 ScreenCaptureKit，支持 ProRes、HEVC、H.264 等专业编码格式。

## 项目定位

**目标用户**:
- 需要高质量屏幕录制的 Mac 用户
- 追求原生 macOS 体验的开发者
- 开源软件的拥护者
- 需要专业视频编码的内容创作者

**解决的问题**:
- **QuickTime Player 功能有限**: 基础录屏无法满足专业需求
- **商业软件昂贵**: 专业录屏软件价格高
- **非原生体验**: 跨平台工具与 macOS 集成差
- **隐私担忧**: 商业软件可能包含追踪

**使用场景**:
- 屏幕录制和演示制作
- 编程教程录制
- 应用演示视频
- 高质量视频导出

**与同类项目差异**:
- **完全免费开源**: MIT 许可，无付费墙
- **原生 SwiftUI**: 真正的 macOS 原生体验
- **ScreenCaptureKit**: 使用最新 macOS 录屏 API
- **专业编码**: ProRes 422/4444、HEVC、H.264 支持
- **菜单栏集成**: 常驻菜单栏，快速访问

## README 中文简介

**BetterCapture** - 为大众设计的 macOS 屏幕录制工具

永远免费开源，原生外观和感觉 📺

**赞助商**:
如果您正在寻找托管桌面录制 API，请查看 Recall.ai —— 一个录制 Zoom、Google Meet、Microsoft Teams、面对面会议等的 API。

**特性**:

**原生 macOS 集成**: 使用 SwiftUI 和 ScreenCaptureKit 构建，常驻菜单栏

**专业编码**: ProRes 422/4444、HEVC (H.265) 和 H.264 编解码器，支持 Alpha 通道和 HDR

**灵活音频捕获**: 同时录制系统音频和麦克风

**内容过滤**: 排除特定内容不录制

**隐私优先**: 无追踪，无分析，所有录制本地存储

**MIT 许可**: 免费开源

**安装**:

**Homebrew**:
```bash
brew install bettercapture
```

**从源码**:
```bash
git clone https://github.com/jsattler/BetterCapture.git
cd BetterCapture
# 打开 Xcode 项目构建
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 原生 macOS | SwiftUI + ScreenCaptureKit | README | 高 |
| 专业编码 | ProRes/HEVC/H.264 | README | 高 |
| Alpha 通道 | 支持透明通道 | README | 高 |
| HDR 支持 | 高动态范围录制 | README | 高 |
| 音频捕获 | 系统音频 + 麦克风 | README | 高 |
| 内容过滤 | 排除特定内容 | README | 高 |
| 隐私优先 | 无追踪分析 | README | 高 |
| 菜单栏 | 常驻菜单栏 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              BetterCapture 架构                              │
│           (macOS 屏幕录制工具)                               │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              UI 层 (SwiftUI)                       │  │
│  │                                                  │  │
│  │   • 菜单栏界面                                   │  │
│  │   • 设置面板                                     │  │
│  │   • 录制控制                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              ScreenCaptureKit                      │  │
│  │                                                  │  │
│  │   • 屏幕捕获                                     │  │
│  │   • 窗口捕获                                     │  │
│  │   • 内容过滤                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              编码层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ ProRes 422   │ ProRes 4444  │ HEVC         ││  │
│  │   │ (专业)       │ (Alpha)      │ (高效)       ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ H.264        │              │              ││  │
│  │   │ (兼容)       │              │              ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              音频层                                │  │
│  │                                                  │  │
│  │   • 系统音频捕获                                 │  │
│  │   • 麦克风捕获                                   │  │
│  │   • 混音处理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 主应用 | `BetterCapture/` | SwiftUI 应用 | 核心 |
| 测试 | `BetterCaptureTests/` | 测试套件 | 质量 |
| 网站 | `website/` | 官网 | 文档 |
| 分发 | `dist/` | 构建输出 | 部署 |

## 运行与开发方式

**安装**:
```bash
# Homebrew
brew install bettercapture

# 或从 Mac App Store (如果上架)
```

**开发**:
```bash
# 克隆仓库
git clone https://github.com/jsattler/BetterCapture.git
cd BetterCapture

# 打开 Xcode 项目
open BetterCapture.xcodeproj

# 构建并运行
# Cmd+R
```

**使用**:
1. 点击菜单栏图标
2. 选择录制区域/窗口
3. 开始录制
4. 专业编码选项在设置中配置

## 外部接口

**菜单栏操作**:
- 点击图标显示控制菜单
- 选择录制模式
- 开始/停止录制

**编码选项**:
| 编码 | 特点 |
|------|------|
| ProRes 422 | 专业级，编辑友好 |
| ProRes 4444 | 支持 Alpha 通道 |
| HEVC | 高效压缩 |
| H.264 | 广泛兼容 |

## 数据流 / 控制流

```
用户操作 (菜单栏)
    ↓
ScreenCaptureKit 捕获
    ↓
视频编码 (ProRes/HEVC/H.264)
    ↓
音频捕获和混音
    ↓
本地文件保存
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Swift | 主要语言 | 高 |
| SwiftUI | UI 框架 | 高 |
| ScreenCaptureKit | 录屏 API | 高 |
| AVFoundation | 音视频处理 | 高 |
| ProRes | 专业编码 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 简洁 | 中 |
| 上手难度 | 低 | Homebrew 一键安装 | 低 |
| 架构复杂度 | 中 | 录屏 + 编码 | 中 |
| 外部依赖 | 低 | 系统框架为主 | 低 |
| Stars | 中 | 1.1k stars | 中 |
| 维护状态 | 中 | 开源项目 | 中 |

**注意事项**:
- 仅支持 macOS
- 需要 macOS 13+ (ScreenCaptureKit)
- ProRes 文件较大
- 首次使用需授权屏幕录制权限

**与商业软件对比**:
| 特性 | BetterCapture | 商业软件 |
|------|--------------|----------|
| 价格 | 免费 | 昂贵 |
| 开源 | 是 | 否 |
| ProRes | 支持 | 部分支持 |
| 追踪 | 无 | 可能有 |

## 关联概念

- [[ScreenCaptureKit]] - macOS 录屏 API
- [[SwiftUI]] - Apple UI 框架
- [[ProRes]] - Apple 专业编码格式
- [[HEVC]] - 高效视频编码
- [[macOS]] - 苹果操作系统
- [[Screen-Recording]] - 屏幕录制技术

---

> 来源: [GitHub](https://github.com/jsattler/BetterCapture) | 置信度: 基于 GitHub README
> 👤 **作者**: jsattler
> ⭐ **Stars**: 1.1k
> 🔗 **官网**: [GitHub](https://github.com/jsattler/BetterCapture)
> 📜 **许可证**: MIT
