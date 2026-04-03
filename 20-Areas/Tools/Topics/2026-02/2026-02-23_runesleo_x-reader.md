---
title: "runesleo/x-reader: 通用内容阅读器 (869 stars)"
github: "https://github.com/runesleo/x-reader"
owner: runesleo
repo: x-reader
date: 2026-02-23
batch_date: 2026-02-23
type: github-project
tags: [github, python, reader, content, mcp, claude-code, youtube, twitter]
pinboard_tags: [reader, ai]
source_used: github-readme-extract
source_url: "https://github.com/runesleo/x-reader"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# runesleo/x-reader: 通用内容阅读器

## 一句话概述

通用内容阅读器，从任何平台（微信公众号、Telegram、X/Twitter、YouTube、Bilibili、小红书、RSS）获取、转录和摘要内容，支持CLI、Python库、MCP服务器和Claude Code Skill四层架构。

## 项目定位

**目标用户**:
- 需要统一内容获取工具的开发者
- 希望AI自动处理多平台内容的用户
- 需要内容聚合和转录的研究人员
- 构建内容工作流的自动化工程师

**解决的问题**:
- **平台碎片化**: 每个平台需要不同工具获取内容
- **内容格式不一**: 不同平台输出格式差异大
- **音视频处理难**: 视频和播客内容难以提取文本
- **Agent集成难**: 内容获取难以集成到AI Agent流程

**使用场景**:
- 批量获取文章、推文、视频内容
- AI Agent内容分析和摘要
- 播客和视频转录
- 多平台内容监控
- 个人知识库自动归档

**与同类项目差异**:
- **四层架构**: Python CLI → Claude Code Skill → MCP Server，按需使用
- **7+平台支持**: 微信公众号、Telegram、X、YouTube、Bilibili、小红书、RSS
- **音视频转录**: 内置Whisper转录（通过Groq API）
- **统一输出格式**: 标准化JSON和Markdown输出
- **零配置使用**: 大部分功能无需API Key

## README 中文简介

**x-reader** — Universal content reader

Any URL → Platform Detection → Fetch Content → Unified Output

**工作流程**:
```
Any URL → Platform Detection → Fetch Content → Unified Output
             ↓                      ↓
         auto-detect           text: Jina Reader
         7+ platforms          video: yt-dlp subtitles
                               audio: Whisper transcription
                               API: Bilibili / RSS / Telegram
```

**四层架构**:

| 层级 | 功能 | 安装 |
|------|------|------|
| Python CLI/Library | 基础内容获取+统一schema | pip install |
| Claude Code Skills | 视频转录+AI分析 | 复制skills/目录 |
| MCP Server | 暴露为MCP工具 | python mcp_server.py |

**支持平台**:
| 平台 | 文本获取 | 音视频转录 |
|------|---------|-----------|
| YouTube | Jina | yt-dlp字幕 → Groq Whisper |
| Bilibili | API | 通过Claude Code Skill |
| X/Twitter | Jina → Playwright | — |
| 微信公众号 | Jina → Playwright | — |
| 小红书 | Jina → Playwright* | — |
| Telegram | Telethon | — |
| RSS | feedparser | — |
| 小宇宙 | — | 通过Claude Code Skill |
| Apple Podcasts | — | 通过Claude Code Skill |
| 任意网页 | Jina fallback | — |

*XHS需要一次性登录: `x-reader login xhs`

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 7+平台支持 | YouTube/Bilibili/X/微信/小红书/Telegram/RSS | README | 高 |
| 音视频转录 | yt-dlp字幕 + Groq Whisper | README | 高 |
| 统一输出 | UnifiedContent标准化schema | README | 高 |
| 多层架构 | CLI/Library/Skill/MCP四层 | README | 高 |
| 浏览器回退 | Playwright处理反爬 | README | 高 |
| Obsidian集成 | 写入Obsidian Vault | README | 高 |
| 批量处理 | 并发获取多个URL | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              x-reader 架构                                   │
│           (通用内容阅读器)                                  │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              接口层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ CLI          │ MCP Server   │ Claude Skill ││  │
│  │   │ (命令行)     │ (MCP工具)    │ (视频/分析)  ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心引擎层                            │  │
│  │                                                  │  │
│  │   • UniversalReader (URL分发器)                  │  │
│  │   • 平台检测和路由                               │  │
│  │   • UnifiedContent标准化模型                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              获取器层 (Fetchers)                   │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Jina         │ Playwright   │ Bilibili API ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ youtube.py   │ rss.py       │ telegram.py  ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ twitter.py   │ wechat.py    │ xhs.py       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录/文件 | 职责 | 关系 |
|------|----------|------|------|
| CLI | `x_reader/cli.py` | 命令行入口 | 核心 |
| 阅读器 | `x_reader/reader.py` | URL分发器(UniversalReader) | 核心 |
| Schema | `x_reader/schema.py` | 统一数据模型 | 核心 |
| 获取器 | `x_reader/fetchers/` | 各平台获取实现 | 核心 |
| 存储 | `x_reader/utils/storage.py` | JSON+Markdown双输出 | 核心 |
| 登录管理 | `x_reader/login.py` | 浏览器会话保存 | 核心 |
| Skills | `skills/` | Claude Code Skills | 扩展 |
| MCP | `mcp_server.py` | MCP服务器入口 | 扩展 |

## 运行与开发方式

**安装**:

```bash
# 从GitHub安装（推荐）
pip install git+https://github.com/runesleo/x-reader.git

# 带Telegram支持
pip install "x-reader[telegram] @ git+https://github.com/runesleo/x-reader.git"

# 带浏览器回退（Playwright - 用于XHS/微信反爬）
pip install "x-reader[browser] @ git+https://github.com/runesleo/x-reader.git"
playwright install chromium

# 带所有可选依赖
pip install "x-reader[all] @ git+https://github.com/runesleo/x-reader.git"
playwright install chromium
```

**视频/音频依赖**:
```bash
# macOS
brew install yt-dlp ffmpeg

# Linux
pip install yt-dlp
apt install ffmpeg
```

**Whisper转录**:
获取免费Groq API Key: https://console.groq.com/keys
```bash
export GROQ_API_KEY=your_key_here
```

**快速开始**:
```bash
# 获取任意URL
x-reader https://mp.weixin.qq.com/s/abc123

# 获取推文
x-reader https://x.com/elonmusk/status/123456

# 批量获取
x-reader https://url1.com https://url2.com

# 登录平台（一次性，用于浏览器回退）
x-reader login xhs

# 查看收件箱
x-reader list
```

**Python库使用**:
```python
import asyncio
from x_reader.reader import UniversalReader

async def main():
    reader = UniversalReader()
    content = await reader.read("https://mp.weixin.qq.com/s/abc123")
    print(content.title)
    print(content.content[:200])

asyncio.run(main())
```

**Claude Code Skills**:
```bash
# 安装Skill
cp -r skills/video ~/.claude/skills/video
cp -r skills/analyzer ~/.claude/skills/analyzer

# 然后在Claude Code中发送YouTube/Bilibili/播客链接
# Skill会自动触发并生成完整转录+摘要
```

**MCP Server**:
```bash
git clone https://github.com/runesleo/x-reader.git
cd x-reader
pip install -e ".[mcp]"
python mcp_server.py
```

Claude Desktop配置 (`~/.claude/claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "x-reader": {
      "command": "python",
      "args": ["/path/to/x-reader/mcp_server.py"]
    }
  }
}
```

暴露的工具:
- `read_url(url)` - 获取任意URL
- `read_batch(urls)` - 并发获取多个URL
- `list_inbox()` - 查看已获取内容
- `detect_platform(url)` - 从URL识别平台

## 外部接口

**CLI命令**:
| 命令 | 功能 |
|------|------|
| `x-reader <url>` | 获取URL内容 |
| `x-reader login <platform>` | 登录平台（保存会话）|
| `x-reader list` | 查看收件箱 |

**环境变量** (`.env`文件):
| 变量 | 必需 | 说明 |
|------|------|------|
| `TG_API_ID` | Telegram | 从 https://my.telegram.org 获取 |
| `TG_API_HASH` | Telegram | 从 https://my.telegram.org 获取 |
| `GROQ_API_KEY` | Whisper | 从 https://console.groq.com/keys (免费) |
| `INBOX_FILE` | 否 | 收件箱JSON路径 (默认: ./unified_inbox.json) |
| `OUTPUT_DIR` | 否 | Markdown输出目录 |
| `OBSIDIAN_VAULT` | 否 | Obsidian Vault路径 |

**输出格式**:
- JSON: UnifiedContent标准化模型
- Markdown: 结构化内容
- Obsidian: 写入`01-收集箱/x-reader-inbox.md`

## 数据流 / 控制流

```
用户输入URL
    ↓
平台检测 (UniversalReader)
    ↓
分发到对应获取器
    ├─ 文本内容 (文章、推文) → Python获取器 → UnifiedContent → 收件箱
    ├─ 视频 (YouTube、Bilibili) → Python获取元数据 → Video Skill → Whisper转录 → 摘要
    └─ 播客 (小宇宙、Apple Podcasts) → Video Skill → Whisper转录 → 摘要
    ↓
请求分析 → Analyzer Skill → 结构化报告
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (100%) | 高 |
| Jina Reader | 通用回退获取 | 高 |
| Playwright | 浏览器自动化 | 高 |
| yt-dlp | YouTube字幕提取 | 高 |
| Groq Whisper | 音视频转录 | 高 |
| feedparser | RSS解析 | 高 |
| Telethon | Telegram API | 高 |
| MCP | Model Context Protocol | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，架构清晰 | 高 |
| 上手难度 | 低 | pip安装即用 | 低 |
| 架构复杂度 | 中 | 多层架构+多平台 | 中 |
| 外部依赖 | 中 | 部分需要API Key | 中 |
| Stars | 中 | 869 stars | 中 |
| 维护状态 | 高 | 23 commits，1个Release | 高 |

**注意事项**:
- 小红书/微信公众号需要Playwright登录（有反爬）
- Groq Whisper需要API Key（免费）
- Telegram需要API ID和API Hash
- 部分平台可能有速率限制

**作者**:
Built by @runes_leo — 更多AI工具: leolabs.me

## 关联概念

- [[Jina-Reader]] - 通用网页内容提取
- [[Playwright]] - 浏览器自动化工具
- [[yt-dlp]] - YouTube下载工具
- [[Whisper]] - OpenAI语音转录
- [[Groq]] - 高性能AI推理API
- [[MCP]] - Model Context Protocol
- [[Claude-Code]] - Anthropic Claude Code
- [[Telethon]] - Telegram MTProto客户端
- [[feedparser]] - Python RSS解析库
- [[Obsidian]] - 知识库工具

---

> 来源: [GitHub](https://github.com/runesleo/x-reader) | 置信度: 基于 GitHub README
> 👤 **作者**: runes_leo (@runes_leo)
> ⭐ **Stars**: 869
> 🔗 **官网**: [leolabs.me](https://leolabs.me)
> 📜 **许可证**: MIT
