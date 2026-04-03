---
title: "RichardAtCT/claude-code-telegram: Claude Code Telegram 机器人 (2.3k stars)"
github: "https://github.com/RichardAtCT/claude-code-telegram"
owner: RichardAtCT
repo: claude-code-telegram
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, python, telegram, bot, claude-code, remote]
pinboard_tags: [telegram, bot, claude-code]
source_used: github-readme-extract
source_url: "https://github.com/RichardAtCT/claude-code-telegram"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# RichardAtCT/claude-code-telegram: Claude Code Telegram 机器人

## 一句话概述

一个 Telegram 机器人，让您远程访问 Claude Code，通过自然语言与 Claude 聊天管理项目，无需终端命令，支持会话持久化和安全沙箱。

## 项目定位

**目标用户**:
- 需要随时随地访问 Claude Code 的开发者
- 希望通过手机管理代码项目的用户
- 需要自然语言交互而非命令行的团队
- 寻求安全远程代码访问方案的工程师

**解决的问题**:
- **终端依赖**: 传统 Claude Code 只能在终端使用
- **移动访问困难**: 手机难以使用命令行工具
- **上下文丢失**: 不同设备间会话无法同步
- **安全风险**: 远程代码访问的安全隐患
- **通知缺失**: CI/CD 事件无法主动通知

**使用场景**:
- 手机端代码审查和修改
- 旅途中项目问题处理
- Webhook 和 CI/CD 事件通知
- 自然语言代码查询和编辑
- 多人协作代码管理

**与同类项目差异**:
- **自然语言交互**: 用自然语言而非命令与 Claude 交流
- **会话持久化**: 每个项目自动保持会话上下文
- **安全沙箱**: 目录沙箱和审计日志保障安全
- **主动通知**: 支持 webhook、定时任务和 CI/CD 事件通知
- **内置认证**: 内置身份验证机制

## README 中文简介

**Claude Code Telegram Bot** - Telegram 机器人远程访问 Claude Code

**这是什么?**

这个机器人将 Telegram 连接到 Claude Code，为您的代码库提供对话式 AI 界面：

- **自然聊天** — 用自然语言请 Claude 分析、编辑或解释您的代码
- **会话持久化** — 跨对话自动保持每个项目的会话上下文
- **随处编码** — 从任何有 Telegram 的设备进行编码
- **主动通知** — 接收来自 webhook、定时任务和 CI/CD 事件的通知
- **安全保障** — 内置身份验证、目录沙箱和审计日志

**快速开始**:

**演示**:
```
You: Can you help me add error handling to src/api.py?
Bot: I'll analyze src/api.py and add error handling...
[Claude reads your code, suggests improvements, and can apply changes directly]
You: Looks good. Now run the tests to make sure nothing broke.
Bot: Running pytest...
All 47 tests passed. The error handling changes are working correctly.
```

**先决条件**:
- Python 3.11+ — 在此下载

**安装步骤**:

1. 克隆仓库
2. 配置环境变量
3. 运行 bot
4. 在 Telegram 中开始对话

**详细安装**:

```bash
# 克隆仓库
git clone https://github.com/RichardAtCT/claude-code-telegram.git
cd claude-code-telegram

# 安装依赖
pip install -r requirements.txt
# 或使用 poetry
poetry install

# 配置环境变量
cp .env.example .env
# 编辑 .env 文件

# 运行
python -m src
# 或
poetry run python -m src
```

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| Telegram Bot | 基于 Telegram 的接口 | README | 高 |
| 自然语言 | 自然语言代码操作 | README | 高 |
| 会话持久化 | 项目级会话保持 | README | 高 |
| 远程访问 | 任何设备 Telegram 访问 | README | 高 |
| 主动通知 | Webhook/CI/CD 通知 | README | 高 |
| 安全沙箱 | 目录隔离和审计 | README | 高 |
| 内置认证 | 身份验证机制 | README | 高 |
| 代码编辑 | 直接应用代码修改 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Claude Code Telegram Bot 架构                   │
│           (Telegram 远程访问 Claude Code)                    │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Telegram 层                           │  │
│  │                                                  │  │
│  │   • Telegram Bot API                             │  │
│  │   • 消息处理                                     │  │
│  │   • 命令解析                                     │  │
│  │   • 文件传输                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Bot 核心层                          │  │
│  │                                                  │  │
│  │   • 自然语言处理                                 │  │
│  │   • 会话管理                                     │  │
│  │   • 项目隔离                                     │  │
│  │   • 认证授权                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Claude Code 层                        │  │
│  │                                                  │  │
│  │   • Claude Code API                              │  │
│  │   • 代码分析                                     │  │
│  │   • 代码编辑                                     │  │
│  │   • 命令执行                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              安全层                                │  │
│  │                                                  │  │
│  │   • 目录沙箱                                     │  │
│  │   • 审计日志                                     │  │
│  │   • 权限控制                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 源码 | `src/` | Bot 核心代码 | 核心 |
| 配置 | `config/` | 配置文件 | 核心 |
| 文档 | `docs/` | 文档 | 文档 |
| 测试 | `tests/` | 测试套件 | 质量 |

## 运行与开发方式

**安装**:
```bash
# 克隆仓库
git clone https://github.com/RichardAtCT/claude-code-telegram.git
cd claude-code-telegram

# 安装 (Poetry 推荐)
pip install poetry
poetry install

# 或使用 pip
pip install -r requirements.txt
```

**配置**:
```bash
# 复制示例配置
cp .env.example .env

# 编辑 .env
# TELEGRAM_BOT_TOKEN=your_token
# CLAUDE_API_KEY=your_key
# ALLOWED_USERS=user1,user2
```

**运行**:
```bash
# Poetry
poetry run python -m src

# 或 pip
python -m src
```

**systemd 部署**:
参见 SYSTEMD_SETUP.md

## 外部接口

**Telegram 命令**:
| 命令 | 功能 |
|------|------|
| `/start` | 开始会话 |
| `/help` | 帮助信息 |
| `/project <name>` | 切换项目 |
| `/status` | 查看状态 |

**环境变量**:
| 变量 | 说明 |
|------|------|
| `TELEGRAM_BOT_TOKEN` | Telegram Bot Token |
| `CLAUDE_API_KEY` | Claude API Key |
| `ALLOWED_USERS` | 允许的用户列表 |
| `PROJECTS_DIR` | 项目根目录 |

## 数据流 / 控制流

```
Telegram 消息
    ↓
Bot 接收处理
    ↓
认证检查
    ↓
自然语言理解
    ↓
Claude Code 调用
    ↓
代码操作执行
    ↓
审计日志记录
    ↓
Telegram 回复
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| python-telegram-bot | Telegram 库 | 高 |
| Poetry | 包管理 | 高 |
| Claude Code API | AI 后端 | 高 |
| systemd | 服务管理 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细 README | 高 |
| 上手难度 | 中 | 需要配置 Telegram Bot | 中 |
| 架构复杂度 | 中 | Bot + Claude Code 集成 | 中 |
| 外部依赖 | 中 | 依赖 Telegram 和 Claude API | 中 |
| Stars | 中 | 2.3k stars | 中 |
| 维护状态 | 高 | 活跃开发 | 高 |

**注意事项**:
- 需要 Telegram Bot Token
- 需要 Claude API 访问权限
- 建议配置 ALLOWED_USERS 限制访问
- 生产环境建议 systemd 部署

**安全功能**:
- 目录沙箱限制文件访问
- 审计日志记录所有操作
- 内置用户认证
- 项目级会话隔离

## 关联概念

- [[Claude-Code]] - Anthropic Claude Code
- [[Telegram-Bot]] - Telegram 机器人
- [[Remote-Development]] - 远程开发
- [[Natural-Language-Interface]] - 自然语言界面
- [[Audit-Log]] - 审计日志
- [[Sandbox]] - 沙箱安全
- [[CI-CD-Notifications]] - CI/CD 通知

---

> 来源: [GitHub](https://github.com/RichardAtCT/claude-code-telegram) | 置信度: 基于 GitHub README
> 👤 **作者**: RichardAtCT
> ⭐ **Stars**: 2.3k
> 🔗 **官网**: [GitHub](https://github.com/RichardAtCT/claude-code-telegram)
> 📜 **许可证**: 未明确
