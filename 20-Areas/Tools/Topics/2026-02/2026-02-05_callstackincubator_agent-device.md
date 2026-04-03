---
title: "callstackincubator/agent-device: Agent 移动设备自动化 CLI (1.4k stars)"
github: "https://github.com/callstackincubator/agent-device"
owner: callstackincubator
repo: agent-device
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, mobile-automation, ios, android, agent, openclaw, testing]
pinboard_tags: [agent, mobile]
source_used: github-readme-extract
source_url: "https://github.com/callstackincubator/agent-device"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# callstackincubator/agent-device: Agent 移动设备自动化 CLI

## 一句话概述

agent-device 是一个面向 iOS、tvOS、macOS、Android 和 AndroidTV 的 UI 自动化 CLI，专为 Agent 驱动的工作流设计：检查 UI、确定性操作、会话感知和可重放，类似 Vercel agent-browser 但针对移动设备。

## 项目定位

**目标用户**:
- 需要移动设备自动化的 Agent 开发者
- 移动应用测试工程师
- 使用 Claude Code 进行移动开发的开发者

**解决的问题**:
- **移动设备自动化难**: 移动设备自动化工具复杂且分散
- **Agent 上下文缺失**: 传统工具难以提供 Agent 需要的结构化 UI 状态
- **会话管理缺失**: 缺乏会话感知的自动化流程
- **可重放性差**: 自动化脚本难以重复执行

**使用场景**:
- Agent 驱动的移动应用测试
- iOS/Android 设备自动化
- 确定性 UI 交互 (点击、输入、滚动)
- E2E 测试套件执行
- 可重放的自动化脚本

**与同类项目差异**:
- **专为 Agent 设计**: 结构化 UI 快照，token 高效
- **跨平台**: 支持 iOS、tvOS、macOS、Android、AndroidTV
- **会话感知**: open → interact → close 完整生命周期
- **可重放脚本**: .ad 脚本格式，可保存和重放
- **Skill 支持**: 提供 agent-device skill 和 dogfood skill

## README 中文简介

**agent-device** - 用于 iOS、tvOS、macOS、Android、AndroidTV 的 UI 自动化 CLI

**项目目标**:
- 给 Agent 提供实用的方式来理解移动 UI 状态
- 保持自动化流程的 token 效率
- 让常见交互可靠到可以重复执行
- 将会话、选择器、可重放流程作为基础

**核心概念**:

| 概念 | 说明 |
|------|------|
| **Sessions** | 打开目标 → 会话内交互 → 干净关闭 |
| **Snapshots** | 检查当前无障碍树，获得紧凑形式和当前屏幕 refs |
| **Refs vs Selectors** | Refs 用于发现，Selectors 用于持久重放和断言 |
| **Tests** | 运行确定性的 .ad 脚本作为轻量级 E2E 测试 |
| **Replay scripts** | 保存 .ad 流程，用 `replay` 或 `test` 重放 |

**命令流程**:
```bash
# 典型流程
agent-device apps --platform ios          # 发现应用
agent-device open SampleApp --platform ios # 打开应用
agent-device snapshot -i                   # 检查屏幕
agent-device press @e3                     # 点击元素
agent-device diff snapshot -i              # 对比变化
agent-device fill @e5 "test"               # 填充输入
agent-device press @e5                     # 点击
agent-device type " more" --delay-ms 80    # 输入文字
agent-device close                         # 关闭会话
```

**测试功能**:
- `test` 支持元数据感知的重试（最多 3 次附加尝试）
- 每测试超时控制
- Flaky pass 报告
- Runner 管理的工件在 `.agent-device/test-artifacts`
- 每次尝试写入 `replay.ad` 和 `result.txt`
- 失败尝试保留日志和工件

**安装**:
```bash
npm install -g agent-device
```

**自动更新检查**:
- CLI 执行交互式运行时自动检查更新
- 有新版本时建议全局重新安装命令
- 设置 `AGENT_DEVICE_NO_UPDATE_NOTIFIER=1` 禁用通知

**macOS 注意**:
- 包含本地 `agent-device-macos-helper` 源包
- 按需构建用于桌面权限检查、警告处理、辅助快照
- 发布版本应使用签名/公证的 helper 构建
- 源码检出回退到本地 Swift 构建

**性能指标**:
```bash
agent-device perf --json    # 或 metrics --json
```

| 平台 | 启动时间 | CPU | 内存 |
|------|----------|-----|------|
| Android | ✅ 采样 | ✅ 采样 | ✅ 采样 |
| macOS/iOS 模拟器 | ✅ 采样 | ✅ 采样 | ✅ 采样 |
| 物理 iOS 设备 | ✅ 采样 | ❌ 不可用 | ❌ 不可用 |

**相关资源**:
- Website: https://agent-device.dev
- Docs: 详见网站
- agent-device skill on ClawHub
- dogfood skill (用于自我测试)

**制作方**: Callstack
- React 和 React Native 极客团队
- 联系: hello@callstack.com

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 多平台支持 | iOS、tvOS、macOS、Android、AndroidTV | README | 高 |
| 结构化快照 | 无障碍树检查，refs 发现 | README | 高 |
| 会话管理 | open → interact → close 生命周期 | README | 高 |
| 可重放脚本 | .ad 脚本保存和重放 | README | 高 |
| E2E 测试 | 轻量级测试套件，重试机制 | README | 高 |
| 性能指标 | 启动时间、CPU、内存采样 | README | 高 |
| Skill 支持 | agent-device skill + dogfood skill | README | 高 |
| 自动更新 | 后台检查新版本 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│            agent-device 架构                               │
│           (Agent 移动设备自动化 CLI)                        │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              CLI 层                              │  │
│  │                                                  │  │
│  │   命令:                                          │  │
│  │   ┌────────┬────────┬────────┬────────┐        │  │
│  │   │ apps   │ open   │snapshot│ press  │        │  │
│  │   ├────────┼────────┼────────┼────────┤        │  │
│  │   │ fill   │ scroll │ get    │ wait   │        │  │
│  │   ├────────┼────────┼────────┼────────┤        │  │
│  │   │ rotate │ replay │ test   │ perf   │        │  │
│  │   ├────────┼────────┼────────┼────────┤        │  │
│  │   │ close  │ diff   │        │        │        │  │
│  │   └────────┴────────┴────────┴────────┘        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              会话管理层                            │  │
│  │                                                  │  │
│  │   Sessions: open ──▶ interact ──▶ close        │  │
│  │                                                  │  │
│  │   状态:                                          │  │
│  │   • 应用上下文 (iOS Bundle ID / Android Package)│  │
│  │   • 屏幕方向                                     │  │
│  │   • 当前 snapshot refs                            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              设备控制层                            │  │
│  │                                                  │  │
│  │   ┌─────────────┐ ┌─────────────┐              │  │
│  │   │ iOS/tvOS    │ │  Android    │              │  │
│  │   │             │ │             │              │  │
│  │   │ • 模拟器    │ │ • 模拟器    │              │  │
│  │   │ • 物理设备  │ │ • 物理设备  │              │  │
│  │   │             │ │ • AndroidTV │              │  │
│  │   └─────────────┘ └─────────────┘              │  │
│  │                                                  │  │
│  │   ┌─────────────┐                               │  │
│  │   │ macOS       │                               │  │
│  │   │ (桌面应用)  │                               │  │
│  │   └─────────────┘                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              UI 检查层                             │  │
│  │                                                  │  │
│  │   Snapshot:                                      │  │
│  │   • 无障碍树遍历                                  │  │
│  │   • Refs 分配 (@e1, @e2...)                      │  │
│  │   • 可见性检测 (visible-first)                   │  │
│  │   • 滚动/列表发现提示                             │  │
│  │                                                  │  │
│  │   Selectors: 持久性标识                           │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              交互执行层                            │  │
│  │                                                  │  │
│  │   操作:                                          │  │
│  │   ┌────────┬────────┬────────┬────────┐        │  │
│  │   │ press  │ fill   │ type   │ scroll │        │  │
│  │   ├────────┼────────┼────────┼────────┤        │  │
│  │   │ rotate │ get    │ wait   │        │        │  │
│  │   └────────┴────────┴────────┴────────┘        │  │
│  │                                                  │  │
│  │   响应: 简短成功确认 (非 JSON 模式)              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              测试与重放层                            │  │
│  │                                                  │  │
│  │   .ad 脚本:                                      │  │
│  │   • 保存: --save-script                          │  │
│  │   • 重放: replay                                 │  │
│  │   • 测试: test (支持重试、超时、flaky)          │  │
│  │                                                  │  │
│  │   工件: .agent-device/test-artifacts             │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              macOS Helper (Swift)                │  │
│  │                                                  │  │
│  │   • 桌面权限检查                                  │  │
│  │   • 警告处理                                      │  │
│  │   • 辅助快照                                      │  │
│  │   • 按需构建 (开发) / 签名构建 (发布)           │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| CLI 入口 | `bin/` | 命令行入口 | 用户接口 |
| 核心代码 | `src/` | TypeScript 核心逻辑 | 引擎 |
| iOS Runner | `ios-runner/` | iOS 设备控制 | 平台 |
| macOS Helper | `macos-helper/` | Swift helper | 平台 |
| Skills | `skills/` | Claude Code Skills | 集成 |
| 测试 | `test/` | 集成测试 | 质量 |
| 网站 | `website/` | 文档网站 | 文档 |

## 运行与开发方式

**安装**:
```bash
npm install -g agent-device
```

**基本命令流程**:
```bash
# 1. 发现应用
agent-device apps --platform ios

# 2. 打开应用
agent-device open SampleApp --platform ios

# 3. 检查屏幕
agent-device snapshot -i

# 4. 交互
agent-device press @e3          # 点击 ref
agent-device fill @e5 "test"    # 填充输入
agent-device press @e5          # 确认
agent-device type " more" --delay-ms 80

# 5. 对比变化
agent-device diff snapshot -i

# 6. 关闭
agent-device close
```

**测试**:
```bash
# 保存脚本
agent-device open SampleApp --platform ios --save-script

# 重放单个脚本
agent-device replay myflow.ad

# 运行测试套件
agent-device test mytests/

# 查看工件
ls .agent-device/test-artifacts/
```

**性能指标**:
```bash
agent-device perf --json
# 或
agent-device metrics --json
```

**macOS 开发**:
- 源码检出会触发本地 Swift 构建
- 发布版本使用签名/公证的 helper

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `apps` | 列出可用应用 |
| `open` | 打开应用/URL |
| `snapshot` | 捕获 UI 状态 |
| `press` | 点击元素 |
| `fill` | 填充输入 |
| `type` | 输入文字 |
| `scroll` | 滚动 |
| `rotate` | 旋转屏幕方向 |
| `get` | 获取元素属性 |
| `wait` | 等待条件 |
| `diff` | 对比 snapshots |
| `replay` | 重放 .ad 脚本 |
| `test` | 运行测试套件 |
| `perf/metrics` | 性能指标 |
| `close` | 关闭会话 |

**平台选项**:
| 平台 | 说明 |
|------|------|
| `ios` | iOS 模拟器/设备 |
| `tvos` | tvOS 模拟器 |
| `macos` | macOS 应用 |
| `android` | Android 模拟器/设备 |
| `androidtv` | AndroidTV |

**Snapshot 选项**:
| 选项 | 说明 |
|------|------|
| `-i` | 交互式 refs |
| 默认 | 可见优先 (visible-first) |

**Skills**:
| Skill | 用途 |
|-------|------|
| `agent-device skill` | 主要操作指导 |
| `dogfood skill` | 自我测试 |
| ClawHub | 在线安装 |

## 数据流 / 控制流

```
用户 CLI 命令
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 会话管理                                                 │
│    • 打开: open ──▶ 启动应用/设备会话                      │
│    • 状态: 维护 bundle ID / package 上下文                │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. UI 检查                                                  │
│    • snapshot ──▶ 遍历无障碍树                             │
│    • 分配 refs (@e1, @e2...)                              │
│    • 标记可见/隐藏内容                                    │
│    • 提供滚动/列表发现提示                                │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 交互执行                                                 │
│    ├─▶ press @ref ──▶ 点击元素                           │
│    ├─▶ fill @ref ──▶ 填充输入                            │
│    ├─▶ type ──▶ 输入文字 (支持延迟)                      │
│    ├─▶ scroll ──▶ 滚动                                   │
│    └─▶ rotate ──▶ 屏幕方向                               │
│    └── 响应: 简短成功确认                                │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 4. 测试与重放                                              │
│    • 保存: --save-script ──▶ .ad 文件                     │
│    • 重放: replay ──▶ 确定性执行                         │
│    • 测试: test ──▶ 套件执行，重试机制                   │
│    • 工件: replay.ad, result.txt, logs                   │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 5. 性能监控                                                │
│    • 启动时间采样 (iOS/Android)                            │
│    • CPU 采样 (Android + Apple 模拟器/macOS)               │
│    • 内存采样 (Android + Apple 模拟器/macOS)               │
└────────────────────────────────────────────────────────────┘
    ↓
关闭: close ──▶ 干净结束会话
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (93.6%) | 高 |
| Swift | macOS Helper (6.3%) | 高 |
| Node.js | CLI 运行时 | 高 |
| npm | 分发 | 高 |
| React Native | Callstack 背景 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 网站 + README + Skills | 高 |
| 上手难度 | 中 | 需要了解移动开发基础 | 中 |
| 架构复杂度 | 中 | 多平台支持 | 中 |
| 外部依赖 | 中 | 依赖设备/模拟器 | 中 |
| Stars | 中 | 1.4k stars |
| 维护状态 | 高 | 活跃开发 (358 commits) | 高 |

**注意事项**:
- 需要配置 iOS/Android 开发环境
- 物理 iOS 设备 CPU/内存指标不可用
- macOS 需要 Swift 构建环境
- 自动更新检查可禁用

## 关联概念

- [[Mobile-Automation]] - 移动设备自动化
- [[Agent-Browser]] - Vercel agent-browser (概念类似)
- [[Claude-Code-Skills]] - Claude Code Skill 系统
- [[iOS-Testing]] - iOS 测试
- [[Android-Testing]] - Android 测试
- [[E2E-Testing]] - 端到端测试

---

> 来源: [GitHub](https://github.com/callstackincubator/agent-device) | 置信度: 基于 GitHub README
> 👤 **作者**: callstackincubator (Callstack)
> ⭐ **Stars**: 1.4k
> 🔗 **网站**: https://agent-device.dev
> 🏢 **组织**: Callstack (React Native 专家团队)
