---
title: "KeygraphHQ/shannon: AI 自动化渗透测试工具 (35.1k stars)"
github: "https://github.com/KeygraphHQ/shannon"
owner: KeygraphHQ
repo: shannon
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, security, pentesting, ai-agent, claude, docker, typescript]
pinboard_tags: [security, pentesting, ai-agent]
source_used: github-readme-extract
source_url: "https://github.com/KeygraphHQ/shannon"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# KeygraphHQ/shannon: AI 自动化渗透测试工具

## 一句话概述

Shannon 是一个自主白盒 AI 渗透测试工具，通过分析源代码识别攻击向量，使用浏览器自动化和命令行工具执行真实漏洞利用(SQL 注入、XSS、SSRF 等)，只报告有可利用 PoC 的漏洞，实现"无利用，不报告"的安全测试闭环。

## 项目定位

**目标用户**:
- 需要持续安全测试的开发团队和安全团队
- 使用 Claude Code、Cursor 等 AI 编码工具的开发者
- 希望自动化安全测试的 DevSecOps 工程师
- 需要验证漏洞可利用性的安全研究员

**解决的问题**:
- **安全测试滞后**: 传统渗透测试每年一次，而代码持续交付
- **高误报率**: 传统 SAST 工具报告大量理论漏洞，无法验证
- **人工测试成本**: 人工渗透测试昂贵且难以规模化
- **AI 编码风险**: AI 辅助编码可能引入安全漏洞
- **验证困难**: 难以区分理论风险和可利用漏洞

**使用场景**:
- CI/CD 流水线中的自动化安全测试
- 每次发布前的快速安全验证
- 白盒代码审计与动态测试结合
- 验证漏洞的可利用性(PoC)
- 学习和研究常见漏洞模式

**与同类项目差异**:
- **白盒+动态**: 结合源代码分析和真实漏洞利用
- **无利用不报告**: 只报告有工作 PoC 的漏洞，零误报
- **全自主运行**: 单命令启动，自动处理 2FA、浏览器导航、利用和报告
- **OWASP 覆盖**: 针对 Injection、XSS、SSRF、认证/授权漏洞
- **并行处理**: 五个漏洞类别并发分析，速度更快

## README 中文简介

**Shannon** - AI 渗透测试工具 (by Keygraph)

Shannon 是一个自主白盒 AI 渗透测试工具，分析源代码识别攻击向量，执行真实漏洞利用来证明漏洞，然后才报告。

**为什么需要 Shannon**:
Claude Code 和 Cursor 让团队持续交付代码，但渗透测试每年才做一次。这造成巨大的安全缺口 —— 其他 364 天你可能在不知不觉中把漏洞交付到生产环境。

Shannon 通过提供按需、自动化的渗透测试来填补这个缺口，可以针对每次构建或发布运行。

**Shannon 实战**:
Shannon 在 OWASP Juice Shop 中发现 20+ 漏洞，包括认证绕过和数据库外泄。

**核心功能**:

**全自主运行**:
- 单命令启动完整渗透测试
- 自动处理 2FA/TOTP 登录(包括 SSO)
- 浏览器导航、漏洞利用、报告生成全自动

**可复现的 PoC 漏洞利用**:
- 最终报告只包含经过验证的可利用发现
- 提供复制粘贴的 PoC
- 无法利用的漏洞不报告

**OWASP 漏洞覆盖**:
- Injection、XSS、SSRF
- 认证/授权破坏
- 更多类别开发中

**代码感知动态测试**:
- 分析源代码指导攻击策略
- 用浏览器和 CLI 工具验证发现

**集成安全工具**:
- Nmap、Subfinder、WhatWeb
- Schemathesis 用于 API 测试

**并行处理**:
- 漏洞分析和利用阶段在所有攻击类别上并发运行

**产品版本**:

**Shannon Lite** (本仓库):
- AGPL-3.0 开源
- 适合本地测试自己的应用
- 核心自主 AI 渗透测试框架

**Shannon Pro** (商业版):
- 一体化应用安全平台
- SAST + SCA + Secrets + 业务逻辑测试 + 自主渗透测试
- CI/CD 集成
- 自托管部署
- 静态-动态关联: 每个报告都有可利用 PoC 和精确代码位置

**快速开始**:

**npx (推荐)**:
```bash
# 1. 配置凭证(交互式向导)
npx @keygraph/shannon setup

# 2. 运行渗透测试
npx @keygraph/shannon start -u https://your-app.com -r /path/to/your-repo
```

**本地构建**:
```bash
git clone https://github.com/KeygraphHQ/shannon.git
cd shannon

# 配置凭证
cat > .env << 'EOF'
ANTHROPIC_API_KEY=your-api-key
CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
EOF

# 安装和构建
pnpm install
pnpm build

# 运行测试
./shannon start -u https://your-app.com -r /path/to/your-repo
```

**配置认证(可选)**:
```yaml
# my-config.yaml
authentication:
  login_type: form
  login_url: "https://your-app.com/login"
  credentials:
    username: "test@example.com"
    password: "yourpassword"
    totp_secret: "LB2E2RX7XFHSTGCK"  # 2FA
  login_flow:
    - "Type $username into the email field"
    - "Type $password into the password field"
    - "Click the 'Sign In' button"
  success_condition:
    type: url_contains
    value: "/dashboard"
```

**架构**:
五阶段多代理架构:
1. **预侦察**: nmap、subfinder、whatweb 扫描 + 代码分析
2. **侦察**: 浏览器自动化探索攻击面
3. **漏洞分析**: 五个类别并发分析(Injection/XSS/Auth/Authz/SSRF)
4. **漏洞利用**: 并行执行真实攻击，无利用不报告
5. **报告**: 生成专业渗透测试报告

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 白盒分析 | 源代码分析识别攻击向量 | README | 高 |
| 动态利用 | 浏览器自动化和 CLI 工具执行真实攻击 | README | 高 |
| 自主运行 | 单命令启动，全自动流程 | README | 高 |
| 认证处理 | 自动处理 2FA/TOTP/SSO | README | 高 |
| 无利用不报告 | 只报告有 PoC 的漏洞，零误报 | README | 高 |
| 并行处理 | 五类漏洞并发分析利用 | README | 高 |
| OWASP 覆盖 | Injection、XSS、SSRF、认证/授权 | README | 高 |
| 集成工具 | Nmap、Subfinder、WhatWeb、Schemathesis | README | 高 |
| 工作空间 | 支持中断恢复，断点续测 | README | 高 |
| 基准测试 | XBOW 96.15% 通过率 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Shannon 架构                                  │
│           (AI 自动化渗透测试工具)                           │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Phase 1: 预侦察                        │  │
│  │                                                  │  │
│  │   • nmap - 端口扫描                              │  │
│  │   • subfinder - 子域名发现                       │  │
│  │   • whatweb - Web 技术指纹识别                   │  │
│  │   • 代码扫描 - 框架识别、入口点分析              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Phase 2: 侦察                          │  │
│  │                                                  │  │
│  │   • 浏览器自动化探索                             │  │
│  │   • 攻击面映射                                   │  │
│  │   • API 端点发现                                 │  │
│  │   • 认证机制分析                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│          ┌───────────────┼───────────────┐               │
│          ▼               ▼               ▼               │
│  ┌───────────┐    ┌───────────┐    ┌───────────┐     │
│  │ Injection │    │    XSS    │    │   SSRF    │     │
│  │   Agent   │    │   Agent   │    │   Agent   │     │
│  └─────┬─────┘    └─────┬─────┘    └─────┬─────┘     │
│        │                │                │             │
│        ▼                ▼                ▼             │
│  ┌───────────┐    ┌───────────┐    ┌───────────┐     │
│  │ Exploit   │    │  Exploit  │    │  Exploit  │     │
│  │ Injection │    │    XSS    │    │   SSRF    │     │
│  └─────┬─────┘    └─────┬─────┘    └─────┬─────┘     │
│        │                │                │             │
│        └────────────────┼────────────────┘             │
│                         ▼                              │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Phase 5: 报告                          │  │
│  │                                                  │  │
│  │   • 综合安全评估报告                             │  │
│  │   • 可复制 PoC                                   │  │
│  │   • 修复建议                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              技术栈                                │  │
│  │                                                  │  │
│  │   • Anthropic Claude Agent SDK (推理引擎)        │  │
│  │   • Temporal (工作流编排)                        │  │
│  │   • Docker (每个扫描独立容器)                    │  │
│  │   • Playwright (浏览器自动化)                    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| CLI | `shannon` | 命令行入口 | 用户接口 |
| 应用 | `apps/` | 主应用逻辑 | 核心 |
| 工作空间 | `workspaces/` | 扫描状态存储 | 数据 |
| 示例报告 | `sample-reports/` | 示例渗透报告 | 参考 |

## 运行与开发方式

**环境要求**:
- Docker
- Node.js 18+ (npx 使用)
- pnpm (本地构建)
- AI Provider 凭证(Anthropic API key / AWS Bedrock / Google Vertex AI)

**npx 快速使用**:
```bash
# 配置
npx @keygraph/shannon setup

# 运行渗透测试
npx @keygraph/shannon start -u https://your-app.com -r /path/to/repo

# 监控进度
npx @keygraph/shannon logs <workspace>
npx @keygraph/shannon status

# 停止
npx @keygraph/shannon stop
```

**本地构建**:
```bash
# 克隆
git clone https://github.com/KeygraphHQ/shannon.git
cd shannon

# 配置
cat > .env << 'EOF'
ANTHROPIC_API_KEY=your-api-key
CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
EOF

# 安装和构建
pnpm install
pnpm build

# 运行
./shannon start -u https://your-app.com -r /path/to/your-repo
```

**工作空间和恢复**:
```bash
# 命名工作空间
npx @keygraph/shannon start -u ... -r ... -w my-audit

# 恢复之前的工作(跳过已完成代理)
npx @keygraph/shannon start -u ... -r ... -w my-audit

# 列出所有工作空间
npx @keygraph/shannon workspaces
```

**云服务支持**:

**AWS Bedrock**:
```bash
export CLAUDE_CODE_USE_BEDROCK=1
export AWS_REGION=us-east-1
export AWS_BEARER_TOKEN_BEDROCK=your-token
export ANTHROPIC_SMALL_MODEL=us.anthropic.claude-haiku-4-5-20251001-v1:0
export ANTHROPIC_MEDIUM_MODEL=us.anthropic.claude-sonnet-4-6
export ANTHROPIC_LARGE_MODEL=us.anthropic.claude-opus-4-6
```

**Google Vertex AI**:
```bash
export CLAUDE_CODE_USE_VERTEX=1
export CLOUD_ML_REGION=us-east5
export ANTHROPIC_VERTEX_PROJECT_ID=your-project
export GOOGLE_APPLICATION_CREDENTIALS=/path/to/sa-key.json
```

**测试本地应用**:
```bash
# Docker 容器无法访问宿主机 localhost
# 使用 host.docker.internal
npx @keygraph/shannon start -u http://host.docker.internal:3000 -r ./my-repo
```

## 外部接口

**CLI 命令**:
| 命令 | 功能 |
|------|------|
| `setup` | 交互式配置向导 |
| `start` | 启动渗透测试 |
| `logs <workspace>` | 查看运行日志 |
| `status` | 检查状态 |
| `stop` | 停止 Shannon |
| `workspaces` | 列出工作空间 |

**配置选项**:
| 参数 | 说明 |
|------|------|
| `-u, --url` | 目标应用 URL |
| `-r, --repo` | 源代码仓库路径 |
| `-c, --config` | 配置文件路径 |
| `-w, --workspace` | 工作空间名称 |
| `-o, --output` | 输出目录 |

**配置认证**:
```yaml
authentication:
  login_type: form
  login_url: "https://..."
  credentials:
    username: "..."
    password: "..."
    totp_secret: "..."  # 2FA
  login_flow:
    - "Type $username into..."
  success_condition:
    type: url_contains
    value: "/dashboard"
```

**输出结构**:
```
workspaces/{hostname}_{sessionId}/
├── session.json          # 指标和会话数据
├── workflow.log          # 工作流日志
├── agents/               # 每代理执行日志
├── prompts/              # 提示词快照
└── deliverables/
    └── comprehensive_security_assessment_report.md
```

## 数据流 / 控制流

```
源代码仓库 + 目标 URL
    ↓
┌────────────────────────────────┐
│ Phase 1: 预侦察                 │
│ • 外部扫描(nmap/subfinder)       │
│ • 代码分析(框架/入口点)          │
└────────────────────────────────┘
    ↓
┌────────────────────────────────┐
│ Phase 2: 侦察                   │
│ • 浏览器自动化探索             │
│ • 攻击面映射                   │
│ • API 端点发现                 │
└────────────────────────────────┘
    ↓
┌────────────────────────────────┐
│ Phase 3: 漏洞分析 (并行×5)      │
│ • Injection Agent              │
│ • XSS Agent                    │
│ • Auth/Authz Agent               │
│ • SSRF Agent                   │
│ 输出: 假设的可利用路径列表       │
└────────────────────────────────┘
    ↓
┌────────────────────────────────┐
│ Phase 4: 漏洞利用 (并行×5)      │
│ • 尝试真实攻击                 │
│ • 无利用不报告                 │
│ 输出: 验证的漏洞 + PoC           │
└────────────────────────────────┘
    ↓
┌────────────────────────────────┐
│ Phase 5: 报告                   │
│ • 生成专业渗透测试报告         │
│ • 可复制 PoC                   │
└────────────────────────────────┘
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (91.1%) | 高 |
| JavaScript | 辅助 (7.3%) | 高 |
| Docker | 容器化 | 高 |
| Anthropic Claude | AI 推理引擎 | 高 |
| Temporal | 工作流编排 | 高 |
| Playwright | 浏览器自动化 | 高 |
| pnpm | 包管理 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细 README、API 文档、示例报告 | 高 |
| 上手难度 | 低 | npx 一键运行 | 低 |
| 架构复杂度 | 中 | 多代理并行架构 | 中 |
| 外部依赖 | 中 | 依赖 AI Provider API | 中 |
| Stars | 高 | 35.1k stars | 高 |
| 维护状态 | 高 | 活跃开发，v1.0.0 已发布 | 高 |

**重要警告**:
- **不要在生产环境运行**: 渗透测试可能修改数据、创建用户、触发副作用
- **仅用于授权测试**: 未经授权扫描系统违反 CFAA 等法律
- **人工验证**: LLM 可能在报告中产生幻觉，需要人工审核
- **成本**: 完整测试约需 $50 USD，耗时 1-1.5 小时
- **Windows 误报**: Windows Defender 可能将报告中的利用代码标记为恶意软件

## 关联概念

- [[Pentesting]] - 渗透测试
- [[DevSecOps]] - 开发安全运维
- [[SAST]] - 静态应用安全测试
- [[DAST]] - 动态应用安全测试
- [[OWASP]] - 开放 Web 应用安全项目
- [[Claude-Agent-SDK]] - Anthropic Agent SDK
- [[White-Box-Testing]] - 白盒测试
- [[Proof-of-Concept]] - 漏洞概念验证

---

> 来源: [GitHub](https://github.com/KeygraphHQ/shannon) | 置信度: 基于 GitHub README
> 👤 **作者**: KeygraphHQ
> ⭐ **Stars**: 35.1k
> 🔗 **官网**: [keygraph.io](https://keygraph.io)
> 📜 **许可证**: AGPL-3.0
