---
title: "nodejs/node: JavaScript 运行时环境 (117k stars)"
github: "https://github.com/nodejs/node"
owner: nodejs
repo: node
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, nodejs, javascript, runtime, backend, v8]
pinboard_tags: [javascript, runtime, backend]
source_used: github-readme-extract
source_url: "https://github.com/nodejs/node"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# nodejs/node: JavaScript 运行时环境

## 一句话概述

Node.js 是一个开源、跨平台的 JavaScript 运行时环境，基于 Chrome V8 引擎，采用事件驱动、非阻塞 I/O 模型，使 JavaScript 可用于构建高性能网络应用、命令行工具和服务器端程序。

## 项目定位

**目标用户**:
- 需要构建高性能网络应用的开发者
- 希望使用 JavaScript 进行全栈开发的工程师
- 构建实时应用、API 服务、微服务的团队
- 命令行工具和自动化脚本开发者

**解决的问题**:
- **JavaScript 局限于浏览器**: 传统 JavaScript 只能在浏览器运行
- **服务器语言碎片化**: 前后端使用不同语言，增加复杂度
- **阻塞 I/O 性能瓶颈**: 传统同步 I/O 模型并发能力有限
- **开发效率**: 需要快速迭代和原型开发
- **生态共享**: 前后端无法复用代码和工具

**使用场景**:
- Web 服务器和 API 后端
- 实时应用(聊天、游戏、协作工具)
- 命令行工具和脚本
- 微服务架构
- 构建工具和任务自动化
- IoT 和嵌入式应用

**与同类项目差异**:
- **事件驱动**: 非阻塞 I/O，高并发处理能力
- **V8 引擎**: Chrome 同款高性能 JavaScript 引擎
- **npm 生态**: 全球最大的开源包管理器
- **单线程模型**: 简化并发编程，避免线程安全问题
- **活跃社区**: OpenJS Foundation 支持，企业级应用广泛

## README 中文简介

**Node.js** - 开源、跨平台的 JavaScript 运行时环境

有关使用 Node.js 的信息，请参见 [Node.js 官网](https://nodejs.org)。

Node.js 项目采用开放治理模式，[OpenJS Foundation](https://openjsf.org/) 为项目提供支持。

贡献者应以协作方式推动项目发展。我们鼓励建设性地交换不同意见和妥协。TSC (技术指导委员会) 保留限制或阻止重复以负面方式影响其他参与者的贡献者的权利。

本项目有 [行为准则](https://github.com/nodejs/node/blob/main/CODE_OF_CONDUCT.md)。

**目录**:
- 支持
- 发布类型
- 下载
- API 文档
- 验证二进制文件
- 从源码构建
- 安全
- 贡献
- 项目团队成员
- 许可证

**支持**:
寻求帮助？查看 [支持说明](https://github.com/nodejs/node/blob/main/SUPPORT.md)。

**发布类型**:

**Current**: 积极开发中。Current 版本的代码在其主版本号分支中(例如 v22.x)。Node.js 每 6 个月发布一个新主版本，允许破坏性变更。这发生在每年的 4 月和 10 月。每年 10 月发布的版本支持周期为 8 个月。每年 4 月发布的版本在当年 10 月转换为 LTS(见下文)。

**LTS**: 接收长期支持的版本，注重稳定性和安全性。每个偶数主版本都会成为 LTS 版本。LTS 版本接收 12 个月的活跃 LTS 支持和额外 18 个月的维护。LTS 版本线有按字母顺序排列的代号，从 v4 Argon 开始。除特殊情况外，没有破坏性变更或功能添加。

**Nightly**: 每天从 Current 分支构建(有变更时)。谨慎使用。

Current 和 LTS 版本遵循语义化版本控制。发布团队成员签名每个 Current 和 LTS 版本。

更多信息参见 [Release README](https://github.com/nodejs/node/blob/main/doc/releases.md)。

**下载**:

二进制文件、安装程序和源代码包可在 https://nodejs.org/en/download/ 获取。

**当前和 LTS 版本**:
https://nodejs.org/download/release/
latest 目录是最新 Current 版本的别名。latest-codename 目录是最新 LTS 版本线的别名。例如，latest-hydrogen 目录包含最新的 Hydrogen (Node.js 18) 版本。

**Nightly 版本**:
https://nodejs.org/download/nightly/
每个目录和文件名包含版本号(例如 v22.0.0)、UTC 日期(例如 20240424)和发布 HEAD 的短 commit SHA。

**API 文档**:

最新 Current 版本的文档位于 https://nodejs.org/api/
每个发布目录的 docs 子目录中有版本特定文档。版本特定文档也在 https://nodejs.org/download/docs/

**验证二进制文件**:

下载目录包含 SHASUMS256.txt.asc 文件，其中有文件的 SHA 校验和和发布者 PGP 签名。

可使用 curl 从 nodejs/release-keys 获取可信密钥环:
```bash
curl -fsLo "/path/to/nodejs-keyring.kbx" \
  "https://github.com/nodejs/release-keys/raw/HEAD/gpg/pubring.kbx"
```

然后验证下载的文件:
```bash
curl -fsO "https://nodejs.org/dist/${VERSION}/SHASUMS256.txt.asc" \
  && gpgv --keyring="/path/to/nodejs-keyring.kbx" \
  --output SHASUMS256.txt < SHASUMS256.txt.asc \
  && shasum --check SHASUMS256.txt --ignore-missing
```

**从源码构建**:

参见 [BUILDING.md](https://github.com/nodejs/node/blob/main/BUILDING.md) 了解如何从源码构建 Node.js 和支持的平台列表。

**安全**:

有关报告 Node.js 中安全漏洞的信息，参见 [SECURITY.md](https://github.com/nodejs/node/blob/main/SECURITY.md)。

**贡献**:

- [贡献指南](https://github.com/nodejs/node/blob/main/CONTRIBUTING.md)
- [工作组](https://github.com/nodejs/node/blob/main/doc/contributing/work-groups.md)
- [战略计划](https://github.com/nodejs/node/blob/main/doc/contributing/strategic-initiatives.md)
- [技术价值和优先级](https://github.com/nodejs/node/blob/main/doc/contributing/technical-values-and-priorities.md)

**项目团队成员**:

**TSC (技术指导委员会)**:
投票成员: aduh95、anonrig、benjamingr、BridgeAR、gireeshpunathil、jasnell、joyeecheung、legendecas、marco-ippolito、mcollina、panva、RafaelGSS、RaisinTen、richardlau、ronag、ruyadorno、ShogunPanda、targos、tniessen

常规成员: BethGriggs、bnoordhuis、cjihrig、codebytere、GeoffreyBooth、MoLow、Trott

荣誉成员: addaleax、apapirovski、ChALkeR、chrisdickinson、danbev、danielleadams、evanlucas、fhinkel、Fishrock123、gabrielschulhof、gibfahn、indutny、isaacs、joshgav、mhdawson、mmarchini、mscdex、MylesBorins、nebrius、ofrobots、orangemocha、piscisaureus、rvagg、sam-github、shigeki、thefourtheye、TimothyGu、trevnorris

**协作者**:
项目有众多协作者，完整列表参见 README。

**发布密钥**:
发布密钥信息参见文档。

**许可证**:
Node.js 可在 [LICENSE](https://github.com/nodejs/node/blob/main/LICENSE) 中找到的许可证下使用。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| JavaScript 运行时 | V8 引擎执行 JS 代码 | README | 高 |
| 事件驱动 | 非阻塞 I/O 模型 | README | 高 |
| 跨平台 | Windows/macOS/Linux 支持 | README | 高 |
| HTTP 服务器 | 内置网络库 | README | 高 |
| 模块系统 | CommonJS + ES Modules | README | 高 |
| npm 生态 | 包管理器和仓库 | README | 高 |
| 流处理 | 强大的流 API | README | 高 |
| 集群支持 | 多进程负载均衡 | README | 高 |
| Buffer | 二进制数据处理 | README | 高 |
| 异步编程 | Promise、async/await | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Node.js 架构                                  │
│           (JavaScript 运行时环境)                           │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              JavaScript 应用层                       │  │
│  │                                                  │  │
│  │   • 用户代码 (JavaScript)                        │  │
│  │   • npm 包生态                                   │  │
│  │   • 核心模块 (http/fs/path/events...)            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Node.js 绑定层                          │  │
│  │                                                  │  │
│  │   • C++ 模块绑定                                 │  │
│  │   • N-API / node-api                             │  │
│  │   • 原生插件接口                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心库层 (C/C++)                      │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ V8 Engine    │ libuv        │ OpenSSL      ││  │
│  │   │ (JS 引擎)     │ (异步 I/O)   │ (加密)       ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ c-ares       │ http-parser  │ zlib         ││  │
│  │   │ (DNS)        │ (HTTP 解析)  │ (压缩)       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              操作系统层                              │  │
│  │                                                  │  │
│  │   • Windows (IOCP)                               │  │
│  │   • macOS (kqueue)                               │  │
│  │   • Linux (epoll)                                │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 源码 | `src/` | C++ 核心实现 | 核心 |
| 库 | `lib/` | JavaScript 核心库 | 核心 |
| 测试 | `test/` | 测试套件 | 质量 |
| 文档 | `doc/` | API 文档 | 文档 |
| 工具 | `tools/` | 构建工具 | 工具 |
| 依赖 | `deps/` | 第三方依赖 | 依赖 |

## 运行与开发方式

**快速开始**:

**下载安装**:
```bash
# 官方安装包
https://nodejs.org/en/download/

# 或使用包管理器
# macOS
brew install node

# Ubuntu/Debian
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**验证安装**:
```bash
node --version
npm --version
```

**运行脚本**:
```bash
node myapp.js
```

**REPL 交互模式**:
```bash
node
> 1 + 1
2
> console.log("Hello")
Hello
```

**从源码构建**:
```bash
# 克隆仓库
git clone https://github.com/nodejs/node.git
cd node

# 配置和构建
./configure
make -j4

# 运行测试
make test
```

**Docker**:
```bash
docker run -it node:20
```

## 外部接口

**Node.js API (核心模块)**:
| 模块 | 功能 |
|------|------|
| `http`/`https` | HTTP 服务器/客户端 |
| `fs` | 文件系统操作 |
| `path` | 路径处理 |
| `events` | 事件发射器 |
| `stream` | 流处理 |
| `crypto` | 加密功能 |
| `os` | 操作系统信息 |
| `process` | 进程信息 |
| `buffer` | 二进制数据 |
| `net` | 网络套接字 |
| `cluster` | 多进程集群 |
| `child_process` | 子进程管理 |
| `worker_threads` | 工作线程 |

**npm 命令**:
| 命令 | 功能 |
|------|------|
| `npm install` | 安装依赖 |
| `npm start` | 启动应用 |
| `npm test` | 运行测试 |
| `npm run <script>` | 运行脚本 |
| `npm publish` | 发布包 |
| `npm update` | 更新依赖 |

**版本管理**:
| 版本线 | 状态 | 说明 |
|--------|------|------|
| v23.x | Current | 当前开发版 |
| v22.x | LTS | 长期支持版 |
| v20.x | LTS | 长期支持版 |
| v18.x | LTS | 维护中 |

## 数据流 / 控制流

```
HTTP 请求 (或 I/O 事件)
    ↓
事件循环 (Event Loop)
    ↓
┌────────────────────────────────┐
│ 判断: 是否阻塞操作?            │
└────────────────────────────────┘
    ↓ 是                ↓ 否
┌──────────────┐    ┌─────────────┐
│ 交给 libuv   │    │ 立即执行    │
│ 线程池处理   │    │             │
└──────────────┘    └─────────────┘
    ↓                      ↓
操作完成              回调执行
    ↓                      ↓
事件触发 ←────────────────┘
    ↓
回调函数执行
    ↓
响应返回
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| C++ | 核心实现 (60%+) | 高 |
| JavaScript | 核心库 (30%+) | 高 |
| V8 | JavaScript 引擎 | 高 |
| libuv | 异步 I/O 库 | 高 |
| Python | 构建工具 | 中 |
| GYP | 构建系统 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 官方文档详尽，API 参考完整 | 高 |
| 上手难度 | 低 | JavaScript 开发者直接可用 | 低 |
| 架构复杂度 | 高 | C++ 核心 + V8 + libuv | 高 |
| 外部依赖 | 中 | 依赖 V8、libuv 等 | 中 |
| Stars | 高 | 117k stars | 高 |
| 维护状态 | 高 | OpenJS Foundation，活跃开发 | 高 |
| 使用量 | 极高 | 数百万项目和网站使用 | 极高 |

**LTS 支持策略**:
- Current: 6 个月活跃开发
- Active LTS: 12 个月维护
- Maintenance: 额外 18 个月
- 每年 4 月和 10 月发布新版本

**注意事项**:
- 生产环境建议使用 LTS 版本
- 单线程模型注意 CPU 密集型任务阻塞
- 回调地狱使用 async/await 解决
- 内存泄漏监控和优化
- npm 包安全审计 (`npm audit`)

**社区资源**:
- [Node.js 官网](https://nodejs.org)
- [npm 仓库](https://www.npmjs.com)
- [Node Weekly](https://nodeweekly.com) - 周报
- [Awesome Node.js](https://github.com/sindresorhus/awesome-nodejs) - 精选资源

## 关联概念

- [[JavaScript]] - 编程语言
- [[V8]] - Google JavaScript 引擎
- [[libuv]] - 跨平台异步 I/O 库
- [[npm]] - Node 包管理器
- [[Event-Loop]] - 事件循环
- [[Non-Blocking-IO]] - 非阻塞 I/O
- [[CommonJS]] - 模块规范
- [[OpenJS-Foundation]] - 基金会

---

> 来源: [GitHub](https://github.com/nodejs/node) | 置信度: 基于 GitHub README
> 👤 **作者**: Node.js 社区 (OpenJS Foundation)
> ⭐ **Stars**: 117k
> 🔗 **官网**: [nodejs.org](https://nodejs.org)
> 💰 **赞助**: GitHub Sponsors, OpenCollective
> 📜 **许可证**: Node.js 许可证 (多许可证)
