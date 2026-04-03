---
title: "lukilabs/beautiful-mermaid: 精美 Mermaid 图表渲染器 (8.5k stars)"
github: "https://github.com/lukilabs/beautiful-mermaid"
owner: lukilabs
repo: beautiful-mermaid
date: 2026-02-02
batch_date: 2026-02-02
type: github-project
tags: [github, mermaid, diagram, svg, ascii, typescript, craft]
pinboard_tags: [mermaid, diagram]
source_used: github-readme-extract
source_url: "https://github.com/lukilabs/beautiful-mermaid"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# lukilabs/beautiful-mermaid: 精美 Mermaid 图表渲染器

## 一句话概述

beautiful-mermaid 是一个将 Mermaid 图表渲染为精美 SVG 或 ASCII 艺术的超快渲染器，完全同步、零 DOM 依赖，支持 15 种内置主题和实时主题切换，专为 AI 时代设计。

## 项目定位

**目标用户**:
- 需要在终端显示图表的 CLI 工具开发者
- 希望图表更精美的技术文档作者
- 构建 AI 编程助手的开发者 (Craft Agents 使用)
- 追求同步渲染无闪烁的 React 开发者

**解决的问题**:
- **默认渲染器审美问题**: Mermaid 默认渲染不够专业
- **主题定制复杂**: 自定义颜色需要与 CSS 类搏斗
- **无终端输出**: 无法在 CLI 中显示图表
- **依赖过重**: 默认渲染器代码量大
- **异步渲染闪烁**: useEffect 导致的图表闪烁

**使用场景**:
- AI 编程助手中的图表可视化
- 技术文档和 README 中的精美图表
- CLI 工具的 ASCII 图表输出
- 实时主题切换的文档系统

**与同类项目差异**:
- **双模输出**: SVG (丰富 UI) + ASCII/Unicode (终端)
- **完全同步**: 无 async，支持 React useMemo() 零闪烁
- **极简主题**: 仅需 bg + fg 两色即可生成完整图表
- **15 内置主题**: 支持 Tokyo Night、Catppuccin、Nord 等流行主题
- **零 DOM 依赖**: 纯 TypeScript，随处运行
- **超快渲染**: 100+ 图表 < 500ms

## README 中文简介

**beautiful-mermaid** - 将 Mermaid 图表渲染为精美 SVG 或 ASCII 艺术。

**设计理念**: 在 AI 辅助编程时代，图表是可视化数据流、状态机和系统架构的必备工具。

**核心特性**:
- 6 种图表类型: 流程图、状态图、序列图、类图、ER 图、XY 图表
- 双输出模式: SVG (丰富 UI) + ASCII/Unicode (终端)
- 同步渲染: 无异步，ELK.js 通过 FakeWorker 同步运行
- 15 内置主题: 支持全 Shiki VS Code 主题
- 实时主题切换: CSS 变量，无需重新渲染
- 单/双色模式: 最低仅需 2 个颜色

**快速开始**:
```bash
npm install beautiful-mermaid
# 或
bun add beautiful-mermaid
```

**SVG 渲染** (同步):
```typescript
import { renderMermaidSVG } from 'beautiful-mermaid'

const svg = renderMermaidSVG(`
graph TD
  A[Start] --> B{Decision}
  B -->|Yes| C[Action]
  B -->|No| D[End]
`)
// 同步返回，无 await
```

**ASCII 渲染**:
```typescript
import { renderMermaidASCII } from 'beautiful-mermaid'

const ascii = renderMermaidASCII(`graph LR; A --> B --> C`)
// 输出:
// ┌───┐     ┌───┐     ┌───┐
// │   │     │   │     │   │
// │ A │────►│ B │────►│ C │
// │   │     │   │     │   │
// └───┘     └───┘     └───┘
```

**React 集成** (零闪烁):
```typescript
function MermaidDiagram({ code }: { code: string }) {
  const { svg, error } = React.useMemo(() => {
    try {
      return {
        svg: renderMermaidSVG(code, {
          bg: 'var(--background)',
          fg: 'var(--foreground)',
          transparent: true,
        }),
        error: null,
      }
    } catch (err) {
      return { svg: null, error: err }
    }
  }, [code])

  if (error) return <pre>{error.message}</pre>
  return <div dangerouslySetInnerHTML={{ __html: svg! }} />
}
```

**主题系统**:
```typescript
// 极简模式: 仅需 bg + fg
const svg = renderMermaidSVG(diagram, {
  bg: '#1a1b26',
  fg: '#a9b1d6',
})

// 丰富模式: 可选 enrichment 颜色
const svg = renderMermaidSVG(diagram, {
  bg: '#1a1b26',
  fg: '#a9b1d6',
  line: '#3d59a1',
  accent: '#7aa2f7',
  muted: '#565f89',
})

// 使用内置主题
import { renderMermaidSVG, THEMES } from 'beautiful-mermaid'
const svg = renderMermaidSVG(diagram, THEMES['tokyo-night'])
```

**15 内置主题**: zinc-light/dark, tokyo-night/storm/light, catppuccin-mocha/latte, nord/nord-light, dracula, github-light/dark, solarized-light/dark, one-dark

**Shiki 主题兼容**:
```typescript
import { getSingletonHighlighter } from 'shiki'
import { renderMermaidSVG, fromShikiTheme } from 'beautiful-mermaid'

const highlighter = await getSingletonHighlighter({
  themes: ['vitesse-dark', 'rose-pine']
})
const colors = fromShikiTheme(highlighter.getTheme('vitesse-dark'))
const svg = renderMermaidSVG(diagram, colors)
```

**支持的图表类型**:
- 流程图 (TD/LR/BT/RL)
- 状态图 (stateDiagram-v2)
- 序列图 (sequenceDiagram)
- 类图 (classDiagram)
- ER 图 (erDiagram)
- XY 图表 (xychart-beta: 柱状图、折线图、组合图)

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 同步 SVG 渲染 | ELK.js FakeWorker 同步运行 | README | 高 |
| ASCII/Unicode 输出 | 终端友好的文本图表 | README | 高 |
| 15 内置主题 | Tokyo Night、Catppuccin、Nord 等 | README | 高 |
| 双色主题系统 | color-mix() 自动推导完整配色 | README | 高 |
| CSS 变量支持 | 实时主题切换无需重渲染 | README | 高 |
| 全 Shiki 兼容 | 使用任意 VS Code 主题 | README | 高 |
| 零 DOM 依赖 | 纯 TypeScript，Node/Browser 通用 | README | 高 |
| 6 种图表类型 | 流程、状态、序列、类、ER、XY 图表 | README | 高 |
| React useMemo 友好 | 零闪烁渲染 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│           beautiful-mermaid 架构                         │
│           (精美 Mermaid 图表渲染器)                        │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              API 层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┐ ┌──────────────┐            │  │
│  │   │renderMermaid │ │renderMermaid │            │  │
│  │   │    SVG       │ │   ASCII      │            │  │
│  │   │              │ │              │            │  │
│  │   │  • 同步渲染   │ │  • Unicode   │            │  │
│  │   │  • 异步版本   │ │  • ASCII 模式│            │  │
│  │   └──────────────┘ └──────────────┘            │  │
│  │                                                  │  │
│  │   ┌──────────────┐ ┌──────────────┐            │  │
│  │   │  parseMermaid│ │fromShikiTheme│            │  │
│  │   │   解析器     │ │  Shiki 适配  │            │  │
│  │   └──────────────┘ └──────────────┘            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              渲染引擎层                          │  │
│  │                                                  │  │
│  │   ┌────────────────────────────────────────┐   │  │
│  │   │           ELK.js 布局引擎             │   │  │
│  │   │                                          │   │  │
│  │   │  • FakeWorker 同步运行                  │   │  │
│  │   │  • 图布局算法                           │   │  │
│  │   │  • 层级/路由计算                        │   │  │
│  │   └────────────────────────────────────────┘   │  │
│  │                          │                       │  │
│  │           ┌──────────────┼──────────────┐       │  │
│  │           ▼              ▼              ▼       │  │
│  │   ┌──────────────┐┌──────────────┐┌──────────┐│  │
│  │   │   SVG 生成   ││  ASCII 生成  ││ XY 图表  ││  │
│  │   │              ││              ││          ││  │
│  │   │ • 路径绘制   ││ • 字符布局   ││ • 柱状图 ││  │
│  │   │ • 节点渲染   ││ • 连线绘制   ││ • 折线图 ││  │
│  │   │ • 样式应用   ││ • 边框生成   ││ • 组合图││  │
│  │   └──────────────┘└──────────────┘└──────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              主题系统层                          │  │
│  │                                                  │  │
│  │   双色基础 (Mono Mode)                           │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │      bg      │    │      fg      │        │  │
│  │   │   背景色     │    │   前景色     │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │          │                   │                  │  │
│  │          └─────────┬─────────┘                  │  │
│  │                    ▼                           │  │
│  │         color-mix() 推导                        │  │
│  │    ┌────┬────┬────┬────┬────┬────┐           │  │
│  │    │text│edge│node│fill│strk│lbl │ ...        │  │
│  │    └────┴────┴────┴────┴────┴────┘           │  │
│  │                                                  │  │
│  │   可选 Enrichment: line, accent, muted...        │  │
│  │                                                  │  │
│  │   15 内置主题 ──▶ THEMES 对象                   │  │
│  │   Shiki 适配 ──▶ fromShikiTheme()               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              图表类型层                            │  │
│  │                                                  │  │
│  │   ┌────────┬────────┬────────┬────────┐      │  │
│  │   │流程图  │ 状态图 │ 序列图 │  类图  │      │  │
│  │   ├────────┼────────┼────────┼────────┤      │  │
│  │   │  ER 图 │XY 图表 │        │        │      │  │
│  │   └────────┴────────┴────────┴────────┘      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 文件 | 职责 | 关系 |
|------|------|------|------|
| 主入口 | `index.ts` | API 导出 | 用户接口 |
| SVG 渲染 | `src/svg/` | SVG 生成逻辑 | 渲染核心 |
| ASCII 渲染 | `src/ascii/` | 文本图表生成 | 终端输出 |
| 布局引擎 | ELK.js | 图布局计算 | 底层依赖 |
| 主题定义 | `src/themes/` | 15 内置主题 | 样式系统 |
| Shiki 适配 | `fromShikiTheme` | VS Code 主题转换 | 扩展 |
| XY 图表 | `xychart-*.ts` | 图表专用逻辑 | 扩展类型 |
| 示例数据 | `samples-data.ts` | 测试用例 | 开发 |

## 运行与开发方式

**安装**:
```bash
npm install beautiful-mermaid
# 或
bun add beautiful-mermaid
# 或
pnpm add beautiful-mermaid
```

**基础使用**:
```typescript
import { renderMermaidSVG, renderMermaidASCII } from 'beautiful-mermaid'

// SVG (同步)
const svg = renderMermaidSVG(`graph TD; A --> B`)

// SVG (异步版本)
const svgAsync = await renderMermaidSVGAsync(`graph TD; A --> B`)

// ASCII
const ascii = renderMermaidASCII(`graph LR; A --> B`)
```

**React 零闪烁集成**:
```typescript
const { svg, error } = React.useMemo(() => {
  try {
    return {
      svg: renderMermaidSVG(code, {
        bg: 'var(--background)',
        fg: 'var(--foreground)',
        transparent: true,
      }),
      error: null,
    }
  } catch (err) {
    return { svg: null, error: err }
  }
}, [code])
```

**主题使用**:
```typescript
import { renderMermaidSVG, THEMES } from 'beautiful-mermaid'

// 使用内置主题
const svg = renderMermaidSVG(diagram, THEMES['tokyo-night'])

// 自定义主题
const myTheme = { bg: '#0f0f0f', fg: '#e0e0e0', accent: '#ff6b6b' }
const svg = renderMermaidSVG(diagram, myTheme)
```

**开发**:
```bash
# 克隆
git clone https://github.com/lukilabs/beautiful-mermaid

# 安装依赖
bun install

# 开发模式
bun run dev

# 基准测试
bun run bench
```

## 外部接口

**核心 API**:
| 函数 | 功能 | 返回值 |
|------|------|--------|
| `renderMermaidSVG(text, options?)` | 同步渲染 SVG | string |
| `renderMermaidSVGAsync(text, options?)` | 异步渲染 SVG | Promise<string> |
| `renderMermaidASCII(text, options?)` | 渲染 ASCII | string |
| `parseMermaid(text)` | 解析为图对象 | MermaidGraph |
| `fromShikiTheme(theme)` | Shiki 主题转图表颜色 | DiagramColors |

**RenderOptions**:
| 选项 | 类型 | 默认 | 说明 |
|------|------|------|------|
| bg | string | #FFFFFF | 背景色 |
| fg | string | #27272A | 前景色 |
| line | string? | — | 边/连接器颜色 |
| accent | string? | — | 箭头/高亮 |
| muted | string? | — | 次要文字 |
| surface | string? | — | 节点填充 |
| border | string? | — | 节点边框 |
| font | string | Inter | 字体 |
| transparent | boolean | false | 透明背景 |
| padding | number | 40 | 画布边距 |
| interactive | boolean | false | XY 图表悬停提示 |

**ASCII 选项**:
| 选项 | 类型 | 默认 | 说明 |
|------|------|------|------|
| useAscii | boolean | false | true=ASCII, false=Unicode |
| paddingX/Y | number | 5 | 节点间距 |
| boxBorderPadding | number | 1 | 内边距 |
| colorMode | string | 'auto' | 颜色模式 |

## 数据流 / 控制流

```
Mermaid 文本输入
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 解析 (parseMermaid)                                    │
│    - 词法分析                                              │
│    - 语法分析                                              │
│    - 构建图对象 (MermaidGraph)                            │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. 布局 (ELK.js)                                          │
│    - FakeWorker 同步运行                                   │
│    - 层级布局算法                                         │
│    - 节点位置计算                                         │
│    - 边路由计算                                           │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 渲染 (分支)                                            │
│                                                            │
│    ├─▶ SVG 渲染                                           │
│    │   ├── 路径绘制 (边和连接器)                         │
│    │   ├── 节点渲染 (矩形/圆角)                            │
│    │   ├── 文本布局 (标签和标注)                           │
│    │   └── 样式应用 (CSS 变量)                             │
│    │                                                        │
│    └─▶ ASCII 渲染                                         │
│        ├── 字符网格布局                                    │
│        ├── 连线绘制 (─│┌┐└┘)                              │
│        └── 节点边框生成                                    │
└────────────────────────────────────────────────────────────┘
    ↓
输出: SVG 字符串 / ASCII 字符串
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 核心语言 | 高 |
| ELK.js | 布局引擎 | 高 |
| Bun | 开发环境 | 高 |
| Shiki | 主题兼容 | 高 |
| CSS color-mix() | 颜色推导 | 高 |
| Wrangler | Cloudflare 部署 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README 非常详细，API 参考完整 | 高 |
| 上手难度 | 低 | npm install 即可，API 简洁 | 低 |
| 架构复杂度 | 中 | 涉及图布局、SVG/ASCII 双渲染 | 中 |
| 外部依赖 | 低 | 核心功能零 DOM 依赖 | 低 |
| Stars | 高 | 8.5k stars |
| 维护状态 | 高 | 21 commits，最近版本 v1.1.2 (Feb 26) | 高 |

**注意事项**:
- 基于 ELK.js 布局，复杂大图可能有性能瓶颈
- XY 图表相对较新，功能持续迭代中
- ASCII 渲染基于 mermaid-ascii Go 项目移植
- Craft Agents 生产环境使用，稳定性有保障

**致谢**:
- ASCII 渲染引擎基于 [mermaid-ascii](https://github.com/alexander-grooff/mermaid-ascii) by Alexander Grooff

## 关联概念

- [[Mermaid]] - Mermaid 图表语法
- [[ELK.js]] - Eclipse 布局内核
- [[Shiki]] - 语法高亮/主题系统
- [[SVG-Rendering]] - SVG 图形渲染
- [[ASCII-Art]] - ASCII 艺术
- [[Diagram-as-Code]] - 代码即图表
- [[Craft-Agents]] - Craft 的 AI 助手

---

> 来源: [GitHub](https://github.com/lukilabs/beautiful-mermaid) | 置信度: 基于 GitHub README
> 👤 **作者**: lukilabs (Craft 团队)
> ⭐ **Stars**: 8.5k
> 📦 **npm**: beautiful-mermaid
> 🔗 **产品**: [Craft](https://www.craft.do) Agents
