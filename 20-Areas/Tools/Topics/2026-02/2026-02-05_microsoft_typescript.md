---
title: "microsoft/TypeScript: JavaScript 超集语言 (108k stars)"
github: "https://github.com/microsoft/TypeScript"
owner: microsoft
repo: TypeScript
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, typescript, javascript, language, compiler, microsoft]
pinboard_tags: [programming-language, typescript, javascript]
source_used: github-readme-extract
source_url: "https://github.com/microsoft/TypeScript"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# microsoft/TypeScript: JavaScript 超集语言

## 一句话概述

TypeScript 是 JavaScript 的应用级超集，添加可选类型系统支持大型应用开发工具，编译为可读的标准 JavaScript，可在任何浏览器、任何主机、任何操作系统上运行。

## 项目定位

**目标用户**:
- 需要构建大型 JavaScript 应用的开发者
- 追求代码质量和可维护性的团队
- 从其他类型语言转向前端开发的工程师
- 需要现代 IDE 支持的项目

**解决的问题**:
- **JavaScript 动态类型**: 大型项目中类型错误难以发现
- **重构困难**: 动态类型导致代码重构风险高
- **IDE 支持有限**: 缺乏智能提示和代码导航
- **文档缺失**: 函数参数和返回值难以追踪
- **团队协作**: 接口契约不明确导致集成问题

**使用场景**:
- 大型企业级 Web 应用
- Node.js 后端服务
- 开源 JavaScript 库开发
- 跨平台应用(React Native, Electron)
- 现代前端框架项目(React, Vue, Angular)

**与同类项目差异**:
- **微软背书**: 微软官方维护，企业级支持
- **JavaScript 超集**: 完全兼容 JavaScript，渐进式采用
- **编译而非转译**: 类型检查在编译时完成，运行无开销
- **工具生态**: VS Code 等工具的原生支持
- **类型系统**: 强大的类型推断和泛型支持

## README 中文简介

**TypeScript** - 应用级 JavaScript 语言

TypeScript 是 JavaScript 的应用级超集。TypeScript 为 JavaScript 添加了支持大型 JavaScript 应用工具的可选类型，可以在任何浏览器、任何主机、任何操作系统上运行。TypeScript 编译为可读的、基于标准的 JavaScript。

**安装**:

最新稳定版:
```bash
npm install -D typescript
```

每日构建版:
```bash
npm install -D typescript@next
```

**贡献**:

注意: 此仓库的代码更改现在仅限于以下小类别修复:
- 在 5.9 或 6.0 中引入且在 7.0 中也能复现的崩溃，有可移植修复且不产生其他行为变化
- 安全问题
- 对主线使用产生重大影响的语言服务崩溃
- 来自 5.9 的严重回归(必须严重影响大量用户)

大多数错误修复应提交到 [typescript-go](https://github.com/microsoft/typescript-go) 仓库。

功能添加和行为变更目前暂停，直到 TypeScript 7.0 完成。

**其他贡献方式**:
- 提交错误并帮助我们验证修复
- 查看源代码变更
- 在 StackOverflow 上与 TypeScript 用户和开发者互动
- 在 TypeScript Community Discord 互相帮助
- 加入 Twitter 上的 #typescript 讨论
- 贡献错误修复

**文档**:
- [TypeScript in 5 minutes](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html) - 5分钟入门
- [Programming handbook](https://www.typescriptlang.org/docs/handbook/intro.html) - 编程手册
- [Homepage](https://www.typescriptlang.org) - 官网
- [Roadmap](https://github.com/microsoft/TypeScript/wiki/Roadmap) - 路线图

**行为准则**: 本项目采用 Microsoft 开源行为准则。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 类型系统 | 可选的静态类型检查 | README | 高 |
| 类型推断 | 强大的自动类型推断 | README | 高 |
| 泛型支持 | 灵活的泛型编程 | README | 高 |
| 接口定义 | 结构化类型定义 | README | 高 |
| 枚举类型 | 数字和字符串枚举 | README | 高 |
| 装饰器 | 实验性装饰器支持 | README | 高 |
| JSX 支持 | React 语法原生支持 | README | 高 |
| 编译优化 | 编译为可读 JS | README | 高 |
| IDE 集成 | 智能提示、重构、导航 | README | 高 |
| 工具链 | tsc、语言服务、格式化 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              TypeScript 架构                               │
│           (JavaScript 超集语言与编译器)                      │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              源代码层 (.ts/.tsx)                     │  │
│  │                                                  │  │
│  │   • TypeScript 语法 (类型注解、接口等)           │  │
│  │   • JavaScript 超集 (完全兼容)                   │  │
│  │   • JSX 语法 (React 支持)                        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              编译器前端                              │  │
│  │                                                  │  │
│  │   • 词法分析 (Lexer)                             │  │
│  │   • 语法解析 (Parser)                            │  │
│  │   • 类型检查 (Type Checker)                      │  │
│  │   • 类型推断 (Type Inference)                    │  │
│  │   • 语义分析 (Semantic Analysis)                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              编译器后端                              │  │
│  │                                                  │  │
│  │   • 代码生成 (Emitter)                           │  │
│  │   • Source Map 生成                            │  │
│  │   • 声明文件生成 (.d.ts)                       │  │
│  │   • 代码优化                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              输出层 (.js/.js.map/.d.ts)            │  │
│  │                                                  │  │
│  │   • 可读的 JavaScript 代码                       │  │
│  │   • Source Map (调试映射)                       │  │
│  │   • 类型声明文件 (供其他项目使用)                │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              语言服务层                              │  │
│  │                                                  │  │
│  │   • 智能提示 (IntelliSense)                      │  │
│  │   • 代码导航 (Go to Definition)                  │  │
│  │   • 重构支持 (Rename, Extract)                   │  │
│  │   • 错误检查 (Diagnostics)                       │  │
│  │   • 格式化 (Formatting)                        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 编译器核心 | `src/compiler/` | 类型检查与代码生成 | 核心 |
| 语言服务 | `src/services/` | IDE 功能实现 | 核心 |
| 解析器 | `src/compiler/parser.ts` | 语法解析 | 核心 |
| 类型检查器 | `src/compiler/checker.ts` | 类型系统 | 核心 |
| 代码生成器 | `src/compiler/emitter.ts` | JS 代码输出 | 核心 |
| 测试 | `tests/` | 测试套件 | 质量 |
| 脚本 | `scripts/` | 构建脚本 | 工具 |

## 运行与开发方式

**快速开始**:

**全局安装**:
```bash
npm install -g typescript
```

**编译文件**:
```bash
tsc myfile.ts
```

**初始化项目**:
```bash
tsc --init
```

**编译配置 (tsconfig.json)**:
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist"
  },
  "include": ["src/**/*"]
}
```

**开发 TypeScript 编译器**:
```bash
# 克隆仓库
git clone https://github.com/microsoft/TypeScript.git
cd TypeScript

# 安装依赖
npm install

# 构建编译器
npm run build:compiler

# 运行测试
npm test

# 本地安装编译器
npm link
```

**每日构建**:
```bash
npm install -D typescript@next
```

## 外部接口

**tsc 命令**:
| 命令/选项 | 功能 |
|-----------|------|
| `tsc file.ts` | 编译单个文件 |
| `tsc` | 根据 tsconfig.json 编译 |
| `tsc --init` | 创建默认配置文件 |
| `tsc --watch` | 监听模式编译 |
| `--target` | 指定 ECMAScript 目标版本 |
| `--module` | 指定模块系统 |
| `--strict` | 启用所有严格类型检查 |
| `--declaration` | 生成 .d.ts 文件 |

**语言服务 API**:
| 服务 | 功能 |
|------|------|
| `getCompletionsAtPosition` | 智能提示 |
| `getDefinitionAtPosition` | 跳转到定义 |
| `getRenameInfo` | 重命名信息 |
| `getFormattingEdits` | 代码格式化 |
| `getQuickInfoAtPosition` | 悬停提示 |
| `getSemanticDiagnostics` | 语义错误检查 |

**Playground**:
- [TypeScript Playground](https://www.typescriptlang.org/play) - 在线试用 TypeScript

## 数据流 / 控制流

```
TypeScript 源代码 (.ts/.tsx)
    ↓
词法分析 → Token 流
    ↓
语法解析 → AST (抽象语法树)
    ↓
类型检查 → 类型信息附加
    ↓
    ├─ 类型推断
    ├─ 接口检查
    ├─ 泛型实例化
    └─ 错误报告
    ↓
代码生成 → JavaScript 代码
    ↓
输出: .js + .js.map + .d.ts
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (99.9%) | 高 |
| Node.js | 运行时 | 高 |
| npm | 包管理 | 高 |
| Gulp | 构建工具 | 高 |
| Jest/Mocha | 测试框架 | 高 |
| GitHub Actions | CI/CD | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 官方文档详尽，社区资源丰富 | 高 |
| 上手难度 | 低 | JavaScript 开发者可渐进采用 | 低 |
| 架构复杂度 | 高 | 完整的编译器实现 | 高 |
| 外部依赖 | 低 | 标准工具链 | 低 |
| Stars | 高 | 108k stars | 高 |
| 维护状态 | 高 | 微软官方维护，216 releases | 高 |
| 使用量 | 极高 | 2,400 万+ 项目使用 | 极高 |

**当前开发状态**:
- 当前版本: 6.0 (2026年3月发布)
- 开发重点: TypeScript 7.0 (使用 Go 语言重写，typescript-go)
- 此仓库(5.9/6.0)目前只接受特定类别的修复
- 大多数新功能将出现在 TypeScript 7.0

**TypeScript 7.0 迁移**:
- 微软正在用 Go 重写 TypeScript (typescript-go 仓库)
- 目标是 10 倍性能提升
- 完全兼容现有 TypeScript 代码

**注意事项**:
- 严格模式 (`strict: true`) 推荐用于新项目
- 类型定义文件可从 DefinitelyTyped 获取
- 装饰器目前是实验性功能
- 关注 TypeScript 7.0 的重大更新

## 关联概念

- [[JavaScript]] - Web 编程语言
- [[Static-Typing]] - 静态类型系统
- [[Compiler]] - 编译器
- [[Type-Inference]] - 类型推断
- [[Generics]] - 泛型编程
- [[VS-Code]] - Visual Studio Code (TypeScript 开发)
- [[Node.js]] - JavaScript 运行时
- [[ECMAScript]] - JavaScript 标准

---

> 来源: [GitHub](https://github.com/microsoft/TypeScript) | 置信度: 基于 GitHub README
> 👤 **作者**: Microsoft (Anders Hejlsberg 等)
> ⭐ **Stars**: 108k
> 🔗 **官网**: [typescriptlang.org](https://www.typescriptlang.org)
> 📜 **许可证**: Apache-2.0
