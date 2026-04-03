---
title: "VoltAgent/awesome-openclaw-skills: OpenClaw Skills 精选集 (43.8k stars)"
github: "https://github.com/VoltAgent/awesome-openclaw-skills"
owner: VoltAgent
repo: awesome-openclaw-skills
date: 2026-02-03
batch_date: 2026-02-03
type: github-project
tags: [github, openclaw, skills, awesome-list, community, volt]
pinboard_tags: [openclaw, skills]
source_used: github-readme-extract
source_url: "https://github.com/VoltAgent/awesome-openclaw-skills"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# VoltAgent/awesome-openclaw-skills: OpenClaw Skills 精选集

## 一句话概述

awesome-openclaw-skills 是 OpenClaw/Volt 社区最大的 Skill 精选列表，收录 5200+ 个社区构建的 Skills，按 20+ 类别组织，是 OpenClaw 生态中访问量仅次于官方资源的 #1 社区资源。

## 项目定位

**目标用户**:
- OpenClaw/Volt 用户寻找可用 Skills
- 想了解 OpenClaw 生态能力的开发者
- 寻找 Skill 开发灵感的创作者

**解决的问题**:
- **Skills 发现困难**: ClawHub 有 13729 个 Skills，难以筛选
- **质量参差不齐**: 社区 Skills 质量差异大，需要精选
- **分类混乱**: 缺乏系统化的 Skill 分类
- **Spam 和低质量**: 存在批量账户、测试垃圾、恶意 Skills

**使用场景**:
- 按类别发现 Skills（Git、Browser、DevOps、AI 等）
- 了解 OpenClaw 生态的最新能力
- 寻找特定用途的 Skill（Slack、Gmail、AWS 等）
- 作为 Skill 开发参考和灵感来源

**与同类项目差异**:
- **最大精选集**: 5200+ Skills，来自 13729 总量
- **严格过滤**: 排除 7215 个低质量/Spam/恶意 Skills
- **系统化分类**: 20+ 类别，便于发现
- **高访问量**: 月 100 万+ 浏览量，#1 社区资源
- **安全提醒**: 明确标注 Skill 安全风险

## README 中文简介

**awesome-openclaw-skills** - 发现 5200+ 社区构建的 OpenClaw Skills，按类别组织。

**什么是 OpenClaw**: OpenClaw 是一个本地运行的 AI 助手，直接在你的机器上操作。Skills 扩展其能力，让它可以与外部服务交互、自动化工作流、执行专业任务。

**数据来源**: Skills 来自 ClawHub (OpenClaw 的公共 Skill 注册中心) 并分类以便发现。

**过滤标准**: 从 13729 个总量中精选 5211 个，过滤掉的类型：

| 过滤类型 | 排除数量 | 说明 |
|----------|----------|------|
| 可能的 Spam | 4,065 | 批量账户、机器人账户、测试/垃圾 |
| 重复/相似名称 | 1,040 | 重复或名称相似的 Skills |
| 低质量或非英文描述 | 851 | 描述质量差或非英文 |
| 加密货币/区块链/金融/交易 | 886 | 相关 Skills |
| 恶意 | 373 | 安全审计识别 (不包括 VirusTotal) |
| **总计未收录** | **7,215** | |

**安装方式**:

**方式 1 - ClawHub CLI**:
```bash
clawhub install <skill-slug>
```

**方式 2 - 手动安装**:
```bash
# 全局安装
~/.openclaw/skills/

# 工作区安装
<project>/skills/
```

优先级: 工作区 > 本地 > 捆绑

**方式 3 - 聊天安装**:
粘贴 Skill 的 GitHub 仓库链接到助手聊天，让助手自动处理安装。

**贡献要求**:
- Skill 必须已在 github.com/openclaw/skills 仓库发布
- 不接受个人仓库、gist 或外部链接
- PR 中需包含 ClawHub 链接和 GitHub 链接

**主要分类** (20+):

| 类别 | Skills 数量 |
|------|------------|
| Git & GitHub | 167 |
| Coding Agents & IDEs | 1,184 |
| Browser & Automation | 322 |
| Web & Frontend Development | 919 |
| DevOps & Cloud | 393 |
| Image & Video Generation | 170 |
| Search & Research | 345 |
| Marketing & Sales | 102 |
| Communication | 146 |
| Productivity & Tasks | 205 |
| Security & Passwords | 53 |
| Apple Apps & Services | 44 |
| CLI Utilities | 180 |
| ... | ... |

**安全提醒**:
- 列表中的 Skills 经过精选但**未经过审计**
- Skill 可能随时被原作者更新、修改或替换
- 安装前自行审查潜在安全风险
- OpenClaw 与 VirusTotal 合作提供安全扫描
- 推荐工具: Snyk Skill Security Scanner, Agent Trust Hub

**风险提示**: Agent Skills 可能包含：
- Prompt 注入
- Tool 中毒
- 隐藏恶意载荷
- 不安全数据处理模式

**使用建议**: 安装前务必审查源代码，风险自负。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 5200+ Skills | 最大精选 Skill 集合 | README | 高 |
| 20+ 类别 | 系统化分类 | README | 高 |
| 严格过滤 | 排除 7215 个低质量/Spam/恶意 | README | 高 |
| 多安装方式 | ClawHub CLI、手动、聊天 | README | 高 |
| 安全提醒 | 明确标注风险 | README | 高 |
| 高访问量 | 月 100 万+ 浏览 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│           awesome-openclaw-skills 架构                   │
│           (OpenClaw Skills 精选集)                        │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              数据源层                            │  │
│  │                                                  │  │
│  │   ┌────────────────────────────────────────┐   │  │
│  │   │           ClawHub Registry             │   │  │
│  │   │                                          │   │  │
│  │   │  • 13,729 社区 Skills                    │   │  │
│  │   │  • 官方 Skill 注册中心                   │   │  │
│  │   │  • github.com/openclaw/skills           │   │  │
│  │   └────────────────────────────────────────┘   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              过滤层                              │  │
│  │                                                  │  │
│  │   过滤规则 (排除 7,215 个):                       │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ Spam/批量账户 │   4,065    │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ 重复/相似名称 │   1,040    │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ 低质量描述    │    851     │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ 加密货币相关  │    886     │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ 恶意 Skills  │    373     │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              精选集层                              │  │
│  │                                                  │  │
│  │   精选 5,211 Skills                              │  │
│  │                                                  │  │
│  │   分类:                                          │  │
│  │   ┌────┬────┬────┬────┬────┬────┬────┐        │  │
│  │   │Git │Code│Web │Dev │Img │Sec │... │        │  │
│  │   └────┴────┴────┴────┴────┴────┴────┘        │  │
│  │                                                  │  │
│  │   总计 20+ 类别                                  │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              生态工具层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │  外部连接    │  Model 提供商 │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ 1,000+ apps  │ 25+ LLMs     │              │  │
│  │   │ OAuth 管理   │ Anthropic    │              │  │
│  │   │ 权限范围     │ OpenAI       │              │  │
│  │   │              │ 等           │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │  托管部署    │ 安全扫描     │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ Docker/Podman│ VirusTotal   │              │  │
│  │   │ Nix/Ansible  │ Snyk         │              │  │
│  │   │ VPS/云       │ Agent Trust  │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 主列表 | `README.md` | Skills 列表 | 核心 |
| 分类 | `categories/` | 分类目录 | 组织 |
| 贡献指南 | `CONTRIBUTING.md` | 贡献规范 | 社区 |
| CI | `.github/workflows/` | 自动化 | 维护 |

## 运行与开发方式

**使用 - 安装 Skills**:

**方法 1: ClawHub CLI**:
```bash
clawhub install <skill-slug>
```

**方法 2: 手动**:
```bash
# 复制 Skill 文件夹到:
~/.openclaw/skills/           # 全局
<project>/skills/             # 工作区
```

**方法 3: 聊天安装**:
```
粘贴 GitHub 链接到助手聊天，让助手自动安装
```

**优先级**: 工作区 > 本地 > 捆绑

**浏览 Skills**:
1. 访问 GitHub 仓库
2. 按类别浏览 (Git & GitHub、Coding Agents、Browser...)
3. 查看 Skill 详情和安装说明

**贡献 Skill**:
1. 确保 Skill 已发布在 github.com/openclaw/skills
2. 获取 ClawHub 链接 (https://clawhub.ai/author/skill)
3. 获取 GitHub 链接
4. 阅读 CONTRIBUTING.md
5. 提交 PR 包含两个链接

## 外部接口

**Skill 来源**:
| 平台 | 链接 |
|------|------|
| ClawHub | https://clawhub.ai/ |
| GitHub | github.com/openclaw/skills |

**安装工具**:
| 工具 | 功能 |
|------|------|
| clawhub CLI | 官方命令行安装 |
| OpenClaw | 内置 Skill 管理 |
| 助手聊天 | 自动识别并安装 |

**安全工具**:
| 工具 | 功能 |
|------|------|
| VirusTotal | 安全扫描 (集成在 ClawHub) |
| Snyk Skill Security Scanner | 安全审计 |
| Agent Trust Hub | 信任评估 |

**生态工具** (精选展示):
- 外部服务连接: 1,000+ apps，托管 OAuth
- Model 提供商: 25+ LLM (Anthropic, OpenAI...)
- 托管部署: Docker, Podman, Nix, Ansible, VPS

## 数据流 / 控制流

```
ClawHub Registry (13,729 Skills)
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 自动过滤                                                │
│    ├── Spam/批量账户 ──▶ 排除 4,065                        │
│    ├── 重复/相似名称 ──▶ 排除 1,040                        │
│    ├── 低质量描述 ────▶ 排除 851                           │
│    ├── 加密货币 ──────▶ 排除 886                           │
│    └── 恶意 Skills ───▶ 排除 373                           │
└────────────────────────────────────────────────────────────┘
    ↓
精选 5,211 Skills
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. 分类整理                                                │
│    ├── Git & GitHub (167)                                 │
│    ├── Coding Agents & IDEs (1,184)                       │
│    ├── Browser & Automation (322)                         │
│    ├── Web & Frontend (919)                                │
│    ├── DevOps & Cloud (393)                                │
│    ├── ... 20+ 类别                                        │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 社区使用                                                │
│    ├── 浏览发现 (月 100 万+ 浏览)                          │
│    ├── 安装使用                                            │
│    └── 贡献反馈                                            │
└────────────────────────────────────────────────────────────┘
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Markdown | 列表格式 | 高 |
| GitHub Actions | CI | 高 |
| OpenClaw/Volt | 生态 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README 清晰，分类完整 | 高 |
| 上手难度 | 低 | 多种安装方式，易于使用 | 低 |
| 架构复杂度 | 低 | 精选列表，无复杂技术 | 低 |
| 外部依赖 | 中 | 依赖 ClawHub 生态 | 中 |
| Stars | 高 | 43.8k stars |
| 社区活跃度 | 高 | 月 100 万+ 浏览 | 高 |

**注意事项**:
- Skills 经过精选但**未经过审计**
- 作者可能随时更新、修改或替换 Skills
- 安装前自行审查安全风险
- 使用 VirusTotal 和 Snyk 等工具扫描
- 恶意风险包括: prompt 注入、tool 中毒、隐藏载荷

## 关联概念

- [[OpenClaw]] - OpenClaw AI 助手
- [[Volt]] - Volt 平台 (OpenClaw 新品牌)
- [[ClawHub]] - OpenClaw Skill 注册中心
- [[Claude-Code-Skills]] - Claude Code Skill 系统
- [[Awesome-Lists]] - 精选列表模式
- [[Agent-Security]] - Agent 安全

---

> 来源: [GitHub](https://github.com/VoltAgent/awesome-openclaw-skills) | 置信度: 基于 GitHub README
> 👤 **作者**: VoltAgent
> ⭐ **Stars**: 43.8k
> 📊 **Skills**: 5,211 精选 / 13,729 总量
> 🏆 **排名**: #1 社区资源 (仅次于官方)
