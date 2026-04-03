---
title: "KaTeX/KaTeX: 高性能 Web 数学公式渲染 (19.9k stars)"
github: "https://github.com/KaTeX/KaTeX"
owner: KaTeX
repo: KaTeX
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, latex, math, typesetting, javascript, typescript, web]
pinboard_tags: [web, math, latex]
source_used: github-readme-extract
source_url: "https://github.com/KaTeX/KaTeX"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# KaTeX/KaTeX: 高性能 Web 数学公式渲染

## 一句话概述

KaTeX 是一个快速、易用的 JavaScript 库，用于在网页上渲染 TeX 数学公式，基于 Donald Knuth 的 TeX 排版标准，同步渲染无需重排，无依赖且支持服务端渲染，兼容所有主流浏览器。

## 项目定位

**目标用户**:
- 需要在网页显示数学公式的开发者和网站
- 教育平台、科技博客、论文发表系统
- Markdown 编辑器、富文本编辑器开发者
- 需要高性能数学排版的前端工程师

**解决的问题**:
- **MathJax 速度慢**: 传统数学公式渲染库异步加载，导致页面重排
- **移动端性能**: 复杂页面在移动设备上渲染卡顿
- **服务端渲染**: 需要前后端一致的渲染结果
- **依赖过多**: 现有方案依赖繁重，集成复杂
- **打印质量**: 网页数学公式打印效果差

**使用场景**:
- 在线教育平台的数学课程
- 科研论文和预印本网站
- Markdown 编辑器实时预览
- 数学论坛和问答社区
- 移动端数学内容展示

**与同类项目差异**:
- **同步渲染**: KaTeX 同步渲染，无需页面重排
- **极速性能**: 比 MathJax 快数倍的渲染速度
- **打印质量**: 基于 TeX 标准的高质量排版
- **零依赖**: 无外部依赖，易于打包
- **SSR 支持**: Node.js 服务端渲染，输出一致

## README 中文简介

**KaTeX** - 快速、易用的 JavaScript 数学公式渲染库

**核心特点**:
- **快速**: 同步渲染，无需页面重排
- **打印质量**: 基于 Donald Knuth 的 TeX 标准
- **自包含**: 无依赖，易于打包到网站资源
- **服务端渲染**: Node.js 生成相同输出，可预渲染
- **浏览器兼容**: Chrome、Safari、Firefox、Opera、Edge

**LaTeX 支持**:
KaTeX 支持大部分 LaTeX 功能和许多 LaTeX 包。

**快速开始**:

**Starter Template**:
```html
<!DOCTYPE html>
<html>
<head>
  <!-- KaTeX 需要 HTML5 doctype -->
  <link rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/katex@0.16.44/dist/katex.min.css"
    integrity="sha384-irXK0JiCGinqGL+slwVklbhJetrjczNwaP2lANewD8lKAs9n61SbQ3As28iSqXUE"
    crossorigin="anonymous">
  <!-- 延迟加载加速页面渲染 -->
  <script defer
    src="https://cdn.jsdelivr.net/npm/katex@0.16.44/dist/katex.min.js"
    integrity="sha384-m/s9umSlhJbqEdA/j7pQVdGCMx2fHf7GXtgCVhNGOwLuu+1qJQES5AzIE8pn3nKQ"
    crossorigin="anonymous"></script>
  <!-- auto-render 扩展自动渲染文本元素中的数学公式 -->
  <script defer
    src="https://cdn.jsdelivr.net/npm/katex@0.16.44/dist/contrib/auto-render.min.js"
    integrity="sha384-bjyGPfbij8/NDKJhSGZNP/khQVgtHUE5exjm4Ydllo42FwIgYsdLO2lXGmRBf5Mz"
    crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
</head>
<body>
  <!-- 页面内容 -->
</body>
</html>
```

**也可下载自托管**:
下载 KaTeX 文件并自行托管。

**API**:

**katex.render** - 直接渲染到 DOM 元素:
```javascript
katex.render("c = \\pm\\sqrt{a^2 + b^2}", element, {
  throwOnError: false
});
```

**katex.renderToString** - 生成 HTML 字符串(服务端渲染):
```javascript
var html = katex.renderToString("c = \\pm\\sqrt{a^2 + b^2}", {
  throwOnError: false
});
// '<span class="katex">...</span>'
```

**务必包含 CSS 和字体文件**。

如果纯服务端渲染，客户端无需 JavaScript。

**错误处理**:
使用 `throwOnError: false` 选项可将无效输入渲染为红色 TeX 源代码(默认)，错误消息作为悬停提示。

**文档**:
- [KaTeX 官网](https://katex.org) - 使用文档、概念概述和指南
- [API 参考](https://katex.org/docs/api) - API 详细文档
- [支持函数列表](https://katex.org/docs/supported.html) - 支持的 LaTeX 功能
- [Demo 页面](https://katex.org) - 在线试用 KaTeX

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 同步渲染 | 无需异步加载，避免页面重排 | README | 高 |
| TeX 标准 | 基于 Donald Knuth 的 TeX 排版 | README | 高 |
| 无依赖 | 纯 JavaScript，无外部依赖 | README | 高 |
| 服务端渲染 | Node.js 预渲染，输出一致 | README | 高 |
| 浏览器兼容 | Chrome/Safari/Firefox/Opera/Edge | README | 高 |
| LaTeX 支持 | 支持大部分 LaTeX 和扩展包 | README | 高 |
| auto-render | 自动渲染文本元素中的公式 | README | 高 |
| 错误处理 | 优雅处理无效输入 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              KaTeX 架构                                      │
│           (高性能 Web 数学公式渲染)                         │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输入层                                │  │
│  │                                                  │  │
│  │   输入: TeX/LaTeX 数学表达式                     │  │
│  │   示例: "c = \\pm\\sqrt{a^2 + b^2}"              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              解析层 (TypeScript)                   │  │
│  │                                                  │  │
│  │   • TeX 词法分析                                 │  │
│  │   • 语法解析                                     │  │
│  │   • 宏展开                                       │  │
│  │   • 符号处理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              排版层                                │  │
│  │                                                  │  │
│  │   • 盒模型布局 (基于 TeX 算法)                   │  │
│  │   • 字体度量                                     │  │
│  │   • 间距计算                                     │  │
│  │   • 对齐处理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输出层                                │  │
│  │                                                  │  │
│  │   HTML + CSS (类名: .katex)                      │  │
│  │   字体文件 (KaTeX 专用字体)                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              部署方式                              │  │
│  │                                                  │  │
│  │   • CDN (jsdelivr)                               │  │
│  │   • npm 包                                       │  │
│  │   • 自托管                                       │  │
│  │   • 服务端渲染 (Node.js)                         │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心源码 | `src/` | 渲染引擎 | 核心 |
| 字体 | `fonts/` | KaTeX 专用字体 | 资源 |
| 贡献扩展 | `contrib/` | auto-render 等扩展 | 扩展 |
| 测试 | `test/` | 测试套件 | 质量 |
| 文档网站 | `website/` | 官网和文档 | 文档 |
| CLI | `cli.js` | 命令行工具 | 工具 |

## 运行与开发方式

**快速集成**:

**CDN (推荐)**:
```html
<link rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/katex@0.16.44/dist/katex.min.css">
<script defer
  src="https://cdn.jsdelivr.net/npm/katex@0.16.44/dist/katex.min.js"></script>
```

**npm**:
```bash
npm install katex
```

```javascript
import katex from 'katex';

// 客户端渲染
katex.render("x^2", element);

// 服务端渲染
const html = katex.renderToString("x^2");
```

**auto-render 扩展**:
```html
<script defer
  src="https://cdn.jsdelivr.net/npm/katex@0.16.44/dist/contrib/auto-render.min.js"
  onload="renderMathInElement(document.body);"></script>
```

**开发构建**:
```bash
# 克隆仓库
git clone https://github.com/KaTeX/KaTeX.git
cd KaTeX

# 安装依赖
yarn install

# 开发模式
yarn dev

# 构建
yarn build

# 测试
yarn test

# 代码检查
yarn lint
```

**CLI 使用**:
```bash
# 命令行渲染
node cli.js "x^2"

# 从文件渲染
node cli.js -f input.tex
```

## 外部接口

**JavaScript API**:
| 方法 | 功能 | 参数 |
|------|------|------|
| `katex.render(tex, element, options)` | 渲染到 DOM 元素 | tex: 表达式, element: DOM 元素 |
| `katex.renderToString(tex, options)` | 生成 HTML 字符串 | tex: 表达式 |

**Options**:
| 选项 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `throwOnError` | boolean | true | 错误时抛出异常 |
| `errorColor` | string | #cc0000 | 错误颜色 |
| `displayMode` | boolean | false | 行间公式模式 |
| `leqno` | boolean | false | 左编号 |
| `fleqn` | boolean | false | 左对齐公式 |

**CLI 参数**:
| 参数 | 说明 |
|------|------|
| `-f, --file` | 从文件读取输入 |
| `-d, --display-mode` | 行间公式模式 |
| `-t, --no-throw-on-error` | 错误时不抛出异常 |

## 数据流 / 控制流

```
TeX 输入字符串
    ↓
词法分析 (Lexer)
    ↓
语法解析 (Parser)
    ↓
宏展开
    ↓
排版计算 (TeX 盒模型)
    ↓
HTML + CSS 生成
    ↓
浏览器渲染 / 服务端返回
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (66.3%) | 高 |
| JavaScript | 辅助 (19%) | 高 |
| Perl | 字体工具 (7.5%) | 中 |
| HTML/CSS | 输出格式 | 高 |
| SCSS | 样式预处理器 | 高 |
| Webpack | 构建工具 | 高 |
| Yarn | 包管理 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 官网文档、API 参考、示例丰富 | 高 |
| 上手难度 | 低 | CDN 一行引入即可使用 | 低 |
| 架构复杂度 | 中 | TeX 排版算法实现 | 中 |
| 外部依赖 | 无 | 零依赖 | 低 |
| Stars | 高 | 19.9k stars | 高 |
| 维护状态 | 高 | 110 个 releases，活跃维护 | 高 |
| 使用量 | 极高 | 233k+ 项目使用 | 极高 |

**注意事项**:
- 需要 HTML5 doctype
- 务必包含 CSS 和字体文件
- 部分复杂 LaTeX 功能可能不支持
- 服务端渲染时需同时包含 CSS

**与 MathJax 对比**:
| 特性 | KaTeX | MathJax |
|------|-------|---------|
| 渲染速度 | 快(同步) | 较慢(异步) |
| 页面重排 | 无 | 有 |
| 包大小 | 小 | 较大 |
| 功能完整度 | 部分 | 更完整 |
| 扩展性 | 有限 | 丰富 |

## 关联概念

- [[LaTeX]] - 文档排版系统
- [[TeX]] - Donald Knuth 排版引擎
- [[MathJax]] - 另一数学公式渲染库
- [[MathML]] - W3C 数学标记语言
- [[Web-Typesetting]] - Web 排版技术
- [[Server-Side-Rendering]] - 服务端渲染

---

> 来源: [GitHub](https://github.com/KaTeX/KaTeX) | 置信度: 基于 GitHub README
> 👤 **作者**: KaTeX 团队
> ⭐ **Stars**: 19.9k
> 🔗 **官网**: [katex.org](https://katex.org)
> 💰 **赞助**: GitHub Sponsors, OpenCollective
> 📜 **许可证**: MIT
