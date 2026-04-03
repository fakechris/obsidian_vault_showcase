---
title: "gemini-cli-extensions/security: Gemini CLI 安全扩展 (679 stars)"
github: "https://github.com/gemini-cli-extensions/security"
owner: gemini-cli-extensions
repo: security
date: 2026-02-03
batch_date: 2026-02-03
type: github-project
tags: [github, gemini, security, code-analysis, vulnerability, google]
pinboard_tags: [gemini, security]
source_used: github-readme-extract
source_url: "https://github.com/gemini-cli-extensions/security"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# gemini-cli-extensions/security: Gemini CLI 安全扩展

## 一句话概述

Security 是 Google 官方开源的 Gemini CLI 扩展，使用 AI 能力分析代码变更中的安全漏洞，支持 12+ 类漏洞检测，集成 OSV-Scanner 进行依赖扫描，在 OpenSSF CVE Benchmark 上达到 90% 精度和 93% 召回率。

## 项目定位

**目标用户**:
- 需要代码安全审查的开发者
- 希望自动化安全分析的 DevOps 团队
- 使用 Gemini CLI 进行代码审查的用户

**解决的问题**:
- **人工安全审查耗时**: 人工检查代码安全问题效率低
- **漏洞遗漏**: 传统工具难以发现复杂安全漏洞
- **依赖安全风险**: 开源依赖中的已知漏洞难以及时发现
- **PR 安全审查**: 代码变更中的安全问题在合并前难发现

**使用场景**:
- 分析 Pull Request 中的安全漏洞
- 扫描项目依赖的已知漏洞
- CI/CD 中集成安全分析
- 开发过程中实时安全检查

**与同类项目差异**:
- **Google 官方出品**: Gemini CLI 原生扩展，无缝集成
- **AI 驱动**: 利用 Gemini 的上下文理解能力
- **实测数据**: OpenSSF CVE Benchmark 90% 精度、93% 召回
- **12+ 漏洞类型**: 覆盖 Secret、Injection、Auth、LLM Safety 等
- **OSV 集成**: 自动扫描依赖漏洞

## README 中文简介

**Security** - Gemini CLI 安全扩展

**核心能力**:
- AI 驱动的安全分析：利用 Gemini 提供智能、上下文感知的安全分析
- 专注代码变更：专为分析 Pull Request 中的代码变更设计
- 开源：Apache 2.0 许可证
- 可扩展架构：支持未来扩展更多漏洞类型
- 依赖扫描：使用 OSV-Scanner 识别依赖漏洞

**安装**:
```bash
gemini extensions install https://github.com/gemini-cli-extensions/security
```

**使用**:
```bash
# 分析当前分支的代码变更
/security:analyze

# 分析指定目录
/security:analyze Analyze all the source code under the script folder. Skip the docs, config files and package files.

# JSON 格式输出
/security:analyze --json

# 依赖漏洞扫描
/security:scan-deps
```

**漏洞类型**:

| 类别 | 漏洞类型 |
|------|----------|
| **Secret 管理** | Hardcoded secrets |
| **不安全数据处理** | 弱加密算法、敏感信息日志、PII 处理违规、不安全反序列化 |
| **注入漏洞** | XSS、SQL 注入、命令注入、SSRF、SSTI |
| **认证** | 认证绕过、弱会话令牌、不安全密码重置 |
| **LLM Safety** | Prompt 注入、不当输出处理、不安全插件使用 |

**基准测试结果** (OpenSSF CVE Benchmark):
- **精度**: 90% - 检测准确率高
- **召回**: 93% - 覆盖全面

**GitHub 集成**:
- 支持 GitHub Actions 工作流
- 可在 PR 中自动触发安全分析
- 与 Gemini CLI Code Review 集成

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| AI 安全分析 | Gemini 驱动的上下文感知分析 | README | 高 |
| 12+ 漏洞类型 | Secret、Injection、Auth、LLM Safety | README | 高 |
| 依赖扫描 | OSV-Scanner 集成 | README | 高 |
| PR 分析 | 专注于代码变更分析 | README | 高 |
| 基准验证 | OpenSSF CVE Benchmark 90%/93% | README | 高 |
| GitHub 集成 | Actions 工作流支持 | README | 高 |
| JSON 输出 | 结构化报告 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│           Gemini CLI Security 扩展架构                    │
│           (AI 驱动的代码安全分析)                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Gemini CLI 层                       │  │
│  │                                                  │  │
│  │   命令:                                          │  │
│  │   - /security:analyze                           │  │
│  │   - /security:scan-deps                         │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              分析引擎层                          │  │
│  │                                                  │  │
│  │   ┌────────────────────────────────────────┐   │  │
│  │   │           AI 安全分析引擎             │   │  │
│  │   │                                          │   │  │
│  │   │  • Gemini 上下文分析                   │   │  │
│  │   │  • 漏洞模式识别                         │   │  │
│  │   │  • 风险评分                             │   │  │
│  │   │  • 修复建议                             │   │  │
│  │   └────────────────────────────────────────┘   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              漏洞检测层                          │  │
│  │                                                  │  │
│  │   Secret │ Injection │ Auth │ LLM Safety        │  │
│  │   ├──────┼───────────┼──────┼─────────────────┤  │
│  │   │硬编码│ XSS       │绕过  │Prompt 注入      │  │
│  │   │凭证  │ SQL 注入  │弱令牌│输出处理         │  │
│  │   │      │ 命令注入  │密码  │插件使用         │  │
│  │   │      │ SSRF/SSTI │重置  │                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              依赖扫描层                          │  │
│  │                                                  │  │
│  │   OSV-Scanner ──▶ OSV.dev 数据库               │  │
│  │   • 交叉引用项目依赖                           │  │
│  │   • 识别已知漏洞                               │  │
│  │   • 提供修复建议                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              报告输出层                          │  │
│  │                                                  │  │
│  │   • 终端友好格式                                │  │
│  │   • JSON 结构化输出                             │  │
│  │   • GitHub Actions 集成                         │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 命令定义 | `commands/security/` | 命令实现 | 用户接口 |
| MCP 服务器 | `mcp-server/` | Model Context Protocol | 集成 |
| 技能定义 | `skills/` | Skill 文件 | 核心逻辑 |
| 文档 | `docs/` | 使用文档 | 参考 |

## 运行与开发方式

**安装**:
```bash
# 要求 Gemini CLI v0.4.0+
gemini extensions install https://github.com/gemini-cli-extensions/security
```

**基本使用**:
```bash
# 分析代码变更
/security:analyze

# 自定义分析范围
/security:analyze Analyze all the source code under the script folder

# JSON 输出
/security:analyze --json

# 依赖扫描
/security:scan-deps
```

**GitHub Actions 集成**:
1. 已有 run-gemini-cli 工作流：替换 `gemini-review.yml`
2. 无工作流：创建 `.github/workflows/`，复制示例工作流
3. 提交新 PR 或评论 `@gemini-cli /review` 触发

**示例工作流**:
```yaml
name: Gemini Code Review with Security
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Gemini CLI Security Analysis
        uses: google/run-gemini-cli-action@v1
        with:
          command: /security:analyze
```

## 外部接口

**命令**:
| 命令 | 功能 |
|------|------|
| `/security:analyze` | 分析代码变更中的安全漏洞 |
| `/security:scan-deps` | 扫描依赖漏洞 (OSV) |

**选项**:
| 选项 | 说明 |
|------|------|
| `--json` | JSON 格式输出 |
| 自然语言 | 自定义分析范围 |

**漏洞类别**:
| 类别 | 漏洞 |
|------|------|
| Secrets | Hardcoded credentials, API keys, passwords |
| Insecure Data | Weak crypto, logging sensitive data, PII violations |
| Injection | XSS, SQLi, Command injection, SSRF, SSTI |
| Auth | Auth bypass, weak tokens, insecure password reset |
| LLM Safety | Prompt injection, improper output handling |

## 数据流 / 控制流

```
代码变更 / PR
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 代码提取                                                │
│    - git diff --merge-base origin/HEAD                     │
│    - 或自定义范围 (自然语言指定)                           │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. AI 分析 (Gemini)                                        │
│    • 上下文理解                                            │
│    • 漏洞模式匹配                                          │
│    • 风险评分                                              │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 漏洞检测分类                                            │
│    ├── Secret 管理                                        │
│    ├── 不安全数据处理                                      │
│    ├── 注入漏洞                                            │
│    ├── 认证问题                                            │
│    └── LLM Safety                                          │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 4. 依赖扫描 (OSV-Scanner)                                 │
│    - 交叉引用 OSV.dev 数据库                              │
│    - 识别已知 CVE                                          │
│    - 提供修复版本                                         │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 5. 报告生成                                                │
│    ├── 终端友好格式                                        │
│    ├── JSON 结构化                                         │
│    └── 修复建议                                            │
└────────────────────────────────────────────────────────────┘
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (84%) | 高 |
| Gemini API | AI 分析能力 | 高 |
| OSV-Scanner | 依赖漏洞扫描 | 高 |
| GitHub Actions | CI 集成 | 高 |
| MCP | Model Context Protocol | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README 详细，使用说明清晰 | 高 |
| 上手难度 | 低 | 一条命令安装使用 | 低 |
| 架构复杂度 | 中 | 涉及 AI 分析、漏洞检测 | 中 |
| 外部依赖 | 中 | 依赖 Gemini API | 中 |
| Stars | 中 | 679 stars |
| 官方支持 | 高 | Google 官方扩展 | 高 |

**注意事项**:
- 需要 Gemini CLI v0.4.0+
- 首次分析为初步扫描，非完整安全审计
- 建议与其他工具和人工审查结合使用
- 当前仅支持交互式使用，非交互式支持计划中

## 关联概念

- [[Gemini-CLI]] - Google Gemini CLI
- [[Code-Security]] - 代码安全分析
- [[OSV]] - Open Source Vulnerabilities
- [[Vulnerability-Scanning]] - 漏洞扫描
- [[AI-Code-Review]] - AI 代码审查
- [[LLM-Safety]] - LLM 安全

---

> 来源: [GitHub](https://github.com/gemini-cli-extensions/security) | 置信度: 基于 GitHub README
> 👤 **作者**: gemini-cli-extensions (Google)
> ⭐ **Stars**: 679
> 📜 **许可证**: Apache-2.0
> 🔗 **基准**: [OpenSSF CVE Benchmark](https://github.com/ossf/scorecard)
