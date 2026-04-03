---
title: "kevinswiber/mmdflux: Mermaid终端文本渲染工具 (41 stars)"
github: "https://github.com/kevinswiber/mmdflux"
owner: kevinswiber
repo: mmdflux
date: 2026-02-24
batch_date: 2026-02-24
type: github-project
tags: [github, rust, mermaid, diagram, terminal, cli, svg]
pinboard_tags: [diagram, ascii, mermaid]
source_used: github-readme-extract
source_url: "https://github.com/kevinswiber/mmdflux"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# kevinswiber/mmdflux: Mermaid终端文本渲染工具

## 一句话概述

mmdflux是一个基于Rust的图表渲染工具包，将Mermaid图表渲染为终端文本、SVG和结构化JSON，内置自研图布局引擎，支持原生正交路由和Unicode方框字符，无需Node.js或浏览器。

## 项目定位

**目标用户**:
- 需要在终端查看Mermaid图表的开发者
- 寻求轻量级图表渲染工具的技术团队
- 需要将图表集成到CLI工具或Agent流程的开发者
- 关注性能和零依赖的技术架构师

**解决的问题**:
- **Node.js依赖重**: 传统Mermaid需要Node.js和浏览器环境
- **终端显示困难**: 现有工具难以在终端友好显示图表
- **机器解析不易**: SVG难以被下游工具解析和处理
- **路由算法局限**: Mermaid默认路由算法常见问题（边交叉、连接点不佳）

**使用场景**:
- CI/CD流水线中的图表生成
- 终端环境下的文档查看
- AI Agent的图表理解pipeline
- 自动化报告生成
- 开发工具集成

**与同类项目差异**:
- **零运行时依赖**: 单二进制文件，无需Node.js/Puppeteer
- **终端文本优先**: 终端输出是一等公民，非二等模式
- **原生正交路由**: flux-layered引擎，正交边路由，确定性扇入/扇出
- **结构化JSON**: MMDS格式输出，供下游工具消费
- **复合图布局**: 子图作为复合图整体布局，非递归渲染

## README 中文简介

**mmdflux** — Mermaid图表 → 终端文本、SVG、结构化JSON

基于Rust的图表渲染工具包，提供CLI、Rust库和WebAssembly包。内置图布局引擎（原生正交路由）、字符网格渲染器（终端输出）和MMDS（结构化JSON格式）。

**核心特性**:
- **零依赖**: 单二进制文件，无Node.js、无浏览器
- **终端文本一等公民**: 独立网格布局系统，Unicode方框字符
- **原生正交路由**: flux-layered引擎，正交边路径
- **结构化JSON**: MMDS格式，下游工具可消费图几何数据
- **多输出格式**: Unicode文本、ASCII文本、SVG、MMDS JSON

**支持的图表类型**:
- Flowchart（流程图）
- Class（类图）
- Sequence（序列图）

**布局引擎**:
| 引擎 | 适用场景 | 路由 |
|------|---------|------|
| flux-layered (默认) | 流程图/类图文本、SVG、MMDS | 正交/折线/直连 |
| mermaid-layered | 流程图/类图SVG、MMDS | 折线 |

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 终端文本渲染 | Unicode/ASCII方框字符 | README | 高 |
| SVG输出 | 多种边样式和曲线选项 | README | 高 |
| MMDS JSON | 结构化图几何数据 | README | 高 |
| 正交路由 | flux-layered自研引擎 | README | 高 |
| 复合图布局 | 子图全局优化布局 | README | 高 |
| 多格式输入 | Mermaid源码 | README | 高 |
| WebAssembly | WASM绑定支持 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              mmdflux 架构                                    │
│           (Mermaid图表渲染工具包)                             │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              接口层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ CLI          │ Rust Library │ WASM         ││  │
│  │   │ (命令行)     │ (库)         │ (Web)        ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              渲染引擎层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Text Grid    │ SVG          │ MMDS JSON    ││  │
│  │   │ (终端)       │ (矢量)       │ (结构化)     ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              布局引擎层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ flux-layered │ mermaid-layered             │  │
│  │   │ (正交路由)   │ (Mermaid兼容)               │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录/文件 | 职责 | 关系 |
|------|----------|------|------|
| CLI | `src/` (CLI入口) | 命令行工具 | 核心 |
| Rust库 | `crates/mmdflux` | 库实现 | 核心 |
| WASM | `crates/mmdflux-wasm` | WebAssembly绑定 | 扩展 |
| 生态系统 | `packages/` | npm包 | 生态 |
| 示例 | `examples/` | 使用示例 | 参考 |

## 运行与开发方式

**安装**:

**Homebrew (推荐)**:
```bash
brew tap kevinswiber/mmdflux
brew install mmdflux
```

**Cargo**:
```bash
cargo install mmdflux
```

**预编译二进制**:
从GitHub Releases下载平台二进制文件。

**快速开始**:
```bash
# 渲染Mermaid文件为终端文本（默认）
mmdflux diagram.mmd

# 从stdin读取
printf 'graph LR\nA-->B\n' | mmdflux

# 禁用ANSI颜色
NO_COLOR=1 mmdflux --format text diagram.mmd

# SVG输出
mmdflux --format svg diagram.mmd -o diagram.svg

# MMDS JSON输出（含路由几何详情）
mmdflux --format mmds --geometry-level routed diagram.mmd

# 验证模式（检查输入并打印诊断）
mmdflux --lint diagram.mmd
```

**SVG边预设**:
| 预设 | 路由 | 曲线 |
|------|------|------|
| smooth-step (默认) | 正交 | 圆角弧 |
| curved-step | 正交 | Basis样条 |
| step | 正交 | 尖角 |
| polyline | 折线 | 尖角 |
| straight | 直连 | 尖角 |

```bash
# 平滑正交圆角（默认）
mmdflux --format svg diagram.mmd -o diagram.svg

# 曲线正交basis路径
mmdflux --format svg --edge-preset curved-step diagram.mmd -o diagram.svg

# 显式曲线控制
mmdflux --format svg --curve linear-rounded diagram.mmd -o diagram.svg
```

**生态系统包**:
| 包 | 描述 |
|-----|------|
| `mmdflux` | CLI和Rust库 (crates.io) |
| `@mmds/wasm` | WebAssembly绑定 (npm) |
| `@mmds/core` | MMDS规范化、遍历、验证工具 (npm) |
| `@mmds/excalidraw` | MMDS转Excalidraw JSON (npm) |
| `@mmds/tldraw` | MMDS转tldraw JSON (npm) |

**Playground**:
在线编辑器: https://play.mmdflux.com (WASM驱动)

**开发**:
```bash
git clone https://github.com/kevinswiber/mmdflux.git
cd mmdflux

# 验证示例编译
cargo test --examples

# 运行示例
cargo run --example high_level_render
cargo run --example registry_adapter
cargo run --example mmds_replay
```

## 外部接口

**CLI参数**:
| 参数 | 说明 |
|------|------|
| `--format` | 输出格式: text/ascii/svg/mmds |
| `--layout-engine` | 布局引擎: flux-layered/mermaid-layered |
| `--edge-preset` | 边预设: smooth-step/curved-step/step/polyline/straight |
| `--curve` | 曲线: basis/linear/linear-rounded/linear-sharp |
| `--geometry-level` | MMDS几何级别: positioned/routed |
| `--lint` | 验证模式 |
| `--color` | 颜色: auto/always/never |

**Rust API**:
高层API:
- `render_diagram` - 渲染图表
- `detect_diagram` - 检测图表类型
- `validate_diagram` - 验证图表

低层API:
- `mmdflux::builtins::default_registry()` - 内置图表注册表
- `registry` and `payload` - 显式检测/解析流程
- `mmds` - MMDS解析、重放、Mermaid生成

**支持特性**:
| 特性 | 支持 |
|------|------|
| 图表类型 | flowchart, class, sequence |
| 输出格式 | Unicode text, ASCII text, SVG, MMDS JSON |
| 布局方向 | TD, BT, LR, RL (支持子图覆盖) |
| 边样式 | solid, dotted, thick, invisible, cross-arrow, circle-arrow |
| 路由 | orthogonal, polyline, direct |
| 双向转换 | Mermaid ↔ MMDS |

## 数据流 / 控制流

```
Mermaid源文件
    ↓
解析和检测图表类型
    ↓
布局引擎 (flux-layered / mermaid-layered)
    ↓
├─→ 终端文本渲染器 (字符网格 + Unicode方框)
├─→ SVG渲染器 (矢量图形)
└─→ MMDS生成器 (结构化JSON)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Rust | 主要语言 (85.7%) | 高 |
| TypeScript | WASM绑定 (7.8%) | 中 |
| JavaScript | 辅助 (2.3%) | 低 |
| SWIG | 绑定生成 (隐含) | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，含Gallery和MMDS Spec | 高 |
| 上手难度 | 低 | Homebrew一键安装 | 低 |
| 架构复杂度 | 中 | 自研布局引擎+多渲染器 | 中 |
| 外部依赖 | 低 | 零运行时依赖 | 低 |
| Stars | 低 | 41 stars | 低 |
| 维护状态 | 高 | 987 commits，9个Release | 高 |

**注意事项**:
- 序列图目前仅支持text/ascii输出
- 序列图不接受--layout-engine参数
- MMDS格式仍在演进中

**相关资源**:
- Playground: https://play.mmdflux.com
- Gallery: 110个fixture渲染示例
- MMDS Spec: 结构化JSON格式规范
- Edge Routing Design: 路由内部设计文档

## 关联概念

- [[Mermaid]] - 图表绘制工具
- [[Rust]] - 系统编程语言
- [[CLI]] - 命令行界面
- [[SVG]] - 可缩放矢量图形
- [[WebAssembly]] - 浏览器端高性能执行
- [[Unicode-Box-Drawing]] - Unicode方框绘制字符
- [[Graph-Layout]] - 图布局算法
- [[Orthogonal-Routing]] - 正交路由
- [[Excalidraw]] - 手绘风格图表工具
- [[tldraw]] - 无限画布绘图工具

---

> 来源: [GitHub](https://github.com/kevinswiber/mmdflux) | 置信度: 基于 GitHub README
> 👤 **作者**: kevinswiber
> ⭐ **Stars**: 41
> 🔗 **官网**: [play.mmdflux.com](https://play.mmdflux.com)
> 📜 **许可证**: MIT
