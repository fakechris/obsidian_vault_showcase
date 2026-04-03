---
title: "jo-inc/camofox-browser: AI Agent 反检测浏览器 (1.2k stars)"
github: "https://github.com/jo-inc/camofox-browser"
owner: jo-inc
repo: camofox-browser
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, browser-automation, anti-detection, playwright, firefox, camoufox, ai-agent]
pinboard_tags: [browser, automation, anti-detection]
source_used: github-readme-extract
source_url: "https://github.com/jo-inc/camofox-browser"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# jo-inc/camofox-browser: AI Agent 反检测浏览器

## 一句话概述

Camofox Browser 是一个面向 AI Agent 的反检测浏览器服务器，基于 Camoufox (Firefox C++ 级指纹伪造分支) 构建，提供 REST API 和 OpenClaw 插件，支持无障碍快照、Cookie 导入、代理路由、YouTube 转录等功能，绕过 Google、Cloudflare 等主流 bot 检测。

## 项目定位

**目标用户**:
- 需要浏览器自动化但经常被检测拦截的 AI Agent 开发者
- 使用 OpenClaw 进行网页浏览的开发者
- 需要爬取受保护网站数据的开发者
- 构建 web agent、数据采集、自动化测试的工程师

**解决的问题**:
- **Bot 检测拦截**: Playwright、Puppeteer 等工具容易被识别为自动化工具
- **指纹追踪**: Headless Chrome 有特征指纹，容易被追踪和封禁
- **IP/地理位置**: 需要代理和地理位置一致性
- **Cookie 管理**: 需要导入浏览器 Cookie 进行认证访问
- **Token 效率**: 原始 HTML 太大，需要精简的内容表示

**使用场景**:
- 访问受 Cloudflare、Google 保护的网站
- 爬取 LinkedIn、Amazon 等需要登录的平台
- YouTube 视频转录提取
- 多用户会话隔离
- 低资源环境部署(Raspberry Pi、$5 VPS)

**与同类项目差异**:
- **C++ 级反检测**: Camoufox 在 C++ 层面伪造指纹，不是 JavaScript shim
- **Token 高效**: 无障碍快照比原始 HTML 小 90%
- **元素 Refs**: 稳定的 e1, e2, e3 标识符用于可靠交互
- **轻量部署**: 空闲时内存仅 ~40MB，适合共享服务器
- **OpenClaw 集成**: 官方插件支持，一键安装

## README 中文简介

**camofox-browser** - AI Agent 反检测浏览器服务器

基于 Camoufox (Firefox 分支，C++ 级指纹伪造) 构建，askjo.ai 的网页浏览引擎。

**为什么需要 Camofox**:
AI Agent 需要浏览真实网页。Playwright 被拦截，Headless Chrome 被指纹识别，隐身插件反而成为指纹。

Camoufox 在 C++ 实现层面修补 Firefox — navigator.hardwareConcurrency、WebGL 渲染器、AudioContext、屏幕几何、WebRTC — 在 JavaScript 看到之前就已伪造。没有 shim，没有包装器，没有痕迹。

**核心功能**:

**C++ 反检测**:
- 绕过 Google、Cloudflare 和大多数 bot 检测
- 伪造硬件并发数、WebGL 渲染器、音频上下文
- 屏幕几何、WebRTC 都在 C++ 层伪造

**元素 Refs**:
- 稳定的 e1, e2, e3 标识符用于可靠交互
- 无障碍快照提供精简页面表示

**Token 高效**:
- 无障碍快照比原始 HTML 小约 90%
- 减少 LLM token 消耗

**轻量运行**:
- 懒加载浏览器 + 空闲关闭
- 空闲时内存仅 ~40MB
- 可在 Raspberry Pi、$5 VPS、Railway 共享实例上运行

**会话隔离**:
- 每个用户独立的 cookies/storage
- Cookie 导入支持 Netscape 格式

**代理 + GeoIP**:
- 代理路由所有流量
- 自动根据代理 IP 设置 locale/timezone/geolocation
- 浏览器指纹与代理位置一致

**结构化日志**:
- JSON 日志行，带 request ID
- 生产环境可观测性

**YouTube 转录**:
- 通过 yt-dlp 提取任何 YouTube 视频字幕
- 无需 API key

**搜索宏**:
- @google_search、@youtube_search、@amazon_search
- @reddit_subreddit 等 10+ 个预定义宏

**快照截图**:
- 附带 base64 PNG 截图的无障碍快照

**大页面处理**:
- 自动快照截断
- 基于 offset 的分页

**下载捕获**:
- 捕获浏览器下载并通过 API 获取
- 可选 inline base64

**DOM 图片提取**:
- 列出 `<img>` src/alt
- 可选返回 inline data URLs

**快速开始**:

**OpenClaw 插件**:
```bash
openclaw plugins install @askjo/camofox-browser
```

**工具列表**:
- camofox_create_tab
- camofox_snapshot
- camofox_click
- camofox_type
- camofox_navigate
- camofox_scroll
- camofox_screenshot
- camofox_close_tab
- camofox_list_tabs
- camofox_import_cookies

**Standalone**:
```bash
git clone https://github.com/jo-inc/camofox-browser
cd camofox-browser
npm install
npm start  # 首次运行下载 Camoufox (~300MB)
```

默认端口 9377。

**Docker**:
```bash
docker build -t camofox-browser .
docker run -p 9377:9377 camofox-browser
```

**Fly.io / Railway**:
包含 fly.toml 和 railway.toml，使用 `fly deploy` 或连接仓库到 Railway。

**Cookie 导入**:
1. 生成密钥: `openssl rand -hex 32`
2. 设置环境变量: `export CAMOFOX_API_KEY="your-key"`
3. 导出浏览器 cookies 为 Netscape 格式
4. 放置到 `~/.camofox/cookies/`
5. 调用 `camofox_import_cookies` 工具

**代理 + GeoIP**:
```bash
export PROXY_HOST=166.88.179.132
export PROXY_PORT=46040
export PROXY_USERNAME=myuser
export PROXY_PASSWORD=mypass
npm start
```

自动设置 locale、timezone、geolocation 与代理位置一致。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| C++ 反检测 | Camoufox 在 C++ 层伪造浏览器指纹 | README | 高 |
| 绕过检测 | 绕过 Google、Cloudflare 等主流检测 | README | 高 |
| 元素 Refs | 稳定的 e1/e2/e3 标识符用于交互 | README | 高 |
| Token 高效 | 无障碍快照比 HTML 小 90% | README | 高 |
| 轻量部署 | 空闲内存 ~40MB，支持 Raspberry Pi | README | 高 |
| 会话隔离 | 每用户独立的 cookies/storage | README | 高 |
| Cookie 导入 | 支持 Netscape 格式 Cookie 文件 | README | 高 |
| 代理 GeoIP | 自动根据代理 IP 设置 locale/timezone | README | 高 |
| YouTube 转录 | 通过 yt-dlp 提取视频字幕 | README | 高 |
| 搜索宏 | 10+ 预定义搜索宏 | README | 高 |
| 截图支持 | 附带 base64 PNG 截图 | README | 高 |
| 大页面处理 | 自动截断和分页 | README | 高 |
| OpenClaw 插件 | 官方插件支持 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Camofox Browser 架构                           │
│           (AI Agent 反检测浏览器服务器)                     │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              API 层 (REST/HTTP)                   │  │
│  │                                                  │  │
│  │   /tabs              POST/GET/DELETE             │  │
│  │   /tabs/:id/snapshot GET (无障碍快照)           │  │
│  │   /tabs/:id/click    POST (点击元素)            │  │
│  │   /tabs/:id/type     POST (输入文字)            │  │
│  │   /tabs/:id/navigate POST (导航/搜索宏)         │  │
│  │   /youtube/transcript POST (YouTube 字幕)       │  │
│  │   /sessions/:id/cookies POST (Cookie 导入)      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              浏览器控制层 (Playwright)              │  │
│  │                                                  │  │
│  │   • Tab 管理                                     │  │
│  │   • 元素交互 (click/type/scroll)                 │  │
│  │   • 无障碍树提取                                 │  │
│  │   • 截图生成                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Camoufox 浏览器引擎                    │  │
│  │                                                  │  │
│  │   C++ 级伪造:                                    │  │
│  │   • navigator.hardwareConcurrency               │  │
│  │   • WebGL 渲染器                                 │  │
│  │   • AudioContext                                 │  │
│  │   • 屏幕几何                                     │  │
│  │   • WebRTC                                       │  │
│  │   • Locale/Timezone/GeoIP                       │  │
│  │                                                  │  │
│  │   (基于 Firefox 分支)                            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              会话管理层                             │  │
│  │                                                  │  │
│  │   User Session (BrowserContext)                  │  │
│  │   ├── Tab Group (sessionKey)                     │  │
│  │   │   ├── Tab (google.com)                       │  │
│  │   │   └── Tab (github.com)                       │  │
│  │   └── Tab Group (sessionKey2)                    │  │
│  │       └── Tab (amazon.com)                       │  │
│  │                                                  │  │
│  │   自动过期: 30分钟无活动                         │  │
│  │   浏览器关闭: 5分钟无活动会话                    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 文件 | 职责 | 关系 |
|------|------|------|------|
| 服务器入口 | `server.js` | Express HTTP 服务 | 入口 |
| OpenClaw 插件 | `plugin.ts` | OpenClaw 工具定义 | 集成 |
| 浏览器控制 | `server.js` | Playwright 封装 | 核心 |
| 测试 | `tests/` | Jest 测试套件 | 质量 |

## 运行与开发方式

**OpenClaw 插件(推荐)**:
```bash
openclaw plugins install @askjo/camofox-browser
```

**Standalone**:
```bash
git clone https://github.com/jo-inc/camofox-browser
cd camofox-browser
npm install
npm start
```

**Docker**:
```bash
docker build -t camofox-browser .
docker run -p 9377:9377 camofox-browser
```

**环境变量配置**:
```bash
# 端口
export CAMOFOX_PORT=9377

# Cookie 导入(必须设置才能使用)
export CAMOFOX_API_KEY="your-generated-key"

# Cookie 目录
export CAMOFOX_COOKIES_DIR="~/.camofox/cookies"

# 代理
export PROXY_HOST="proxy.example.com"
export PROXY_PORT="8080"
export PROXY_USERNAME="user"
export PROXY_PASSWORD="pass"

# 超时设置
export SESSION_TIMEOUT_MS=1800000        # 30分钟
export BROWSER_IDLE_TIMEOUT_MS=300000   # 5分钟
```

**测试**:
```bash
npm test              # 所有测试
npm run test:e2e      # 端到端测试
npm run test:live     # 实时网站测试
npm run test:debug    # 带服务器输出
```

## 外部接口

**Tab 生命周期**:
| 方法 | 端点 | 说明 |
|------|------|------|
| POST | `/tabs` | 创建 tab |
| GET | `/tabs?userId=X` | 列出所有 tab |
| GET | `/tabs/:id/stats` | Tab 统计 |
| DELETE | `/tabs/:id` | 关闭 tab |
| DELETE | `/tabs/group/:groupId` | 关闭整个组 |
| DELETE | `/sessions/:userId` | 关闭用户所有 tab |

**页面交互**:
| 方法 | 端点 | 说明 |
|------|------|------|
| GET | `/tabs/:id/snapshot` | 无障碍快照(支持 includeScreenshot, offset) |
| POST | `/tabs/:id/click` | 点击元素(by ref 或 CSS selector) |
| POST | `/tabs/:id/type` | 输入文字 |
| POST | `/tabs/:id/press` | 按键 |
| POST | `/tabs/:id/scroll` | 滚动页面 |
| POST | `/tabs/:id/navigate` | 导航 URL 或搜索宏 |
| POST | `/tabs/:id/wait` | 等待 selector 或超时 |
| GET | `/tabs/:id/links` | 提取所有链接 |
| GET | `/tabs/:id/images` | 列出 `<img>` 元素 |
| GET | `/tabs/:id/downloads` | 列出捕获的下载 |
| GET | `/tabs/:id/screenshot` | 截图 |
| POST | `/tabs/:id/back` | 后退 |
| POST | `/tabs/:id/forward` | 前进 |
| POST | `/tabs/:id/refresh` | 刷新 |

**YouTube 转录**:
| 方法 | 端点 | 说明 |
|------|------|------|
| POST | `/youtube/transcript` | 提取 YouTube 视频字幕 |

**会话管理**:
| 方法 | 端点 | 说明 |
|------|------|------|
| POST | `/sessions/:userId/cookies` | 添加 cookies 到用户会话 |

**搜索宏**:
| 宏 | 功能 |
|----|------|
| `@google_search` | Google 搜索 |
| `@youtube_search` | YouTube 搜索 |
| `@amazon_search` | Amazon 搜索 |
| `@reddit_search` | Reddit 搜索 |
| `@reddit_subreddit` | 浏览 subreddit |
| `@wikipedia_search` | Wikipedia 搜索 |
| `@twitter_search` | Twitter 搜索 |
| `@yelp_search` | Yelp 搜索 |
| `@spotify_search` | Spotify 搜索 |
| `@netflix_search` | Netflix 搜索 |
| `@linkedin_search` | LinkedIn 搜索 |
| `@instagram_search` | Instagram 搜索 |
| `@tiktok_search` | TikTok 搜索 |
| `@twitch_search` | Twitch 搜索 |

## 数据流 / 控制流

```
Agent 请求浏览网页
    ↓
Camofox Server API
    ↓
创建/复用 User Session
    ↓
创建 Tab (Camoufox 浏览器)
    ↓
导航到目标 URL
    ↓
C++ 级指纹伪造生效
    ↓
获取无障碍快照 (element refs)
    ↓
返回精简表示给 Agent
    ↓
Agent 决策交互
    ↓
调用 click/type/navigate API
    ↓
重复直到任务完成
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| JavaScript | 主要语言 (90%) | 高 |
| TypeScript | 插件定义 (8.9%) | 高 |
| Node.js | 服务端运行时 | 高 |
| Express | HTTP 服务器 | 高 |
| Playwright | 浏览器控制 | 高 |
| Camoufox | Firefox 反检测分支 | 高 |
| Jest | 测试框架 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细的 README 和 API 文档 | 高 |
| 上手难度 | 低 | 一键安装 OpenClaw 插件 | 低 |
| 架构复杂度 | 中 | 浏览器引擎 + API 服务 | 中 |
| 外部依赖 | 中 | 依赖 Camoufox 下载 | 中 |
| Stars | 中 | 1.2k stars | 中 |
| 维护状态 | 高 | 活跃开发，5 个 releases | 高 |

**注意事项**:
- Cookie 导入需要设置 CAMOFOX_API_KEY
- 首次运行需要下载 Camoufox (~300MB)
- 用于合法授权的数据采集
- 请勿用于非法爬取或绕过安全控制

## 关联概念

- [[Camoufox]] - Firefox 反检测分支
- [[Playwright]] - 浏览器自动化工具
- [[Browser-Automation]] - 浏览器自动化技术
- [[Anti-Detection]] - 反检测技术
- [[Web-Scraping]] - 网页数据采集
- [[OpenClaw]] - AI Agent 框架
- [[Headless-Browser]] - 无头浏览器

---

> 来源: [GitHub](https://github.com/jo-inc/camofox-browser) | 置信度: 基于 GitHub README
> 👤 **作者**: jo-inc (askjo.ai)
> ⭐ **Stars**: 1.2k
> 📜 **许可证**: MIT
