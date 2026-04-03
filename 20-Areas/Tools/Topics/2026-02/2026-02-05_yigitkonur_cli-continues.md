---
title: "yigitkonur/cli-continues: AI编码会话跨工具恢复 (996 stars)"
github: "https://github.com/yigitkonur/cli-continues"
owner: yigitkonur
repo: cli-continues
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, typescript, cli, ai, session-management, context-transfer]
pinboard_tags: [cli, ai, session]
source_used: github-readme-extract
source_url: "https://github.com/yigitkonur/cli-continues"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# yigitkonur/cli-continues: AI编码会话跨工具恢复

## 一句话概述

continues 是一个CLI工具，支持在14个AI编码工具（Claude Code、Codex、Cursor、Gemini等）之间任意切换并恢复会话上下文，解决不同工具间rate limit导致的会话中断问题。

## 项目定位

**目标用户**:
- 使用多个AI编码工具的开发者
- 经常遇到rate limit需要切换工具的用户
- 需要保留会话上下文迁移的用户
- 希望备份和导出会话历史的开发者

**解决的问题**:
- **Rate limit中断**: 30条上下文后需等待数小时或重新开始
- **工具锁定**: 一旦开始就无法切换到其他AI工具
- **上下文丢失**: 文件变更、架构决策、半完成重构全部丢失
- **会话备份**: 无法导出和备份AI会话历史

**使用场景**:
- Claude Code rate limit后切换到Gemini继续
- 从Cursor迁移到Cline保持完整上下文
- 批量备份所有AI工具会话
- 团队协作时共享AI会话上下文
- CI/CD中自动化会话恢复

**与同类项目差异**:
- **14工具支持**: 支持14个AI编码代理的任意切换
- **182条切换路径**: 任意源到任意目标
- **零修改读取**: 只读访问会话文件，不修改源数据
- **丰富上下文**: 包含消息、文件变更、工具活动、token用量
- **多种格式**: 支持交互式TUI、JSON、JSONL、Markdown导出

## README 中文简介

**continues** — 当你在debug中途遇到rate limit时

30条消息上下文——文件变更、架构决策、半完成的重构——现在你要么等几小时，要么在其他工具重新开始。continues抓取你在任意AI编码工具的会话，并切换到另一个工具。对话历史、文件变更、工作状态——全部保留。

**核心特性**:
- **14个AI编码代理**: 任意切换
- **182条切换路径**: 任意源→任意目标
- **零安装**: `npx continues` 直接运行
- **智能提取**: 读取各工具原生格式（JSONL/JSON/SQLite/YAML）
- **结构化交接**: 生成上下文文档，接收代理立即理解工作状态

**支持的工具**:
Claude Code · Codex · GitHub Copilot CLI · Gemini CLI · Cursor · Amp · Cline · Roo Code · Kilo Code · Kiro · Crush · OpenCode · Factory Droid · Antigravity

**工作流程**:
1. **Discovery**: 扫描会话目录
2. **Parsing**: 读取各工具原生格式
3. **Extraction**: 提取近期消息、文件变更、工具活动、AI推理
4. **Handoff**: 生成结构化上下文文档，注入目标工具

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 14工具支持 | Claude/Codex/Cursor/Gemini等 | README | 高 |
| 182切换路径 | 任意源→任意目标 | README | 高 |
| 只读访问 | 不修改源会话文件 | README | 高 |
| 丰富上下文 | 消息+文件+工具活动+token | README | 高 |
| 多格式导出 | Markdown/JSON/JSONL | README | 高 |
| 交互式TUI | 会话选择器 | README | 高 |
| 快速恢复 | 直接恢复最近会话 | README | 高 |
| 批量导出 | 备份所有会话 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              continues 架构                                │
│           (AI编码会话跨工具恢复)                           │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              发现层 (Discovery)                    │  │
│  │                                                  │  │
│  │   • 扫描14个工具的会话目录                       │  │
│  │   • 建立会话索引 (~/.continues/sessions.jsonl)   │  │
│  │   • 5分钟TTL自动刷新                             │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              解析层 (Parsing)                        │  │
│  │                                                  │  │
│  │   ┌────────────┬────────────┬────────────┐    │  │
│  │   │ JSONL      │ JSON       │ SQLite     │    │  │
│  │   ├────────────┼────────────┼────────────┤    │  │
│  │   │ YAML       │            │            │    │  │
│  │   └────────────┴────────────┴────────────┘    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              提取层 (Extraction)                     │  │
│  │                                                  │  │
│  │   • 近期消息 (3-50条，可配置)                    │  │
│  │   • 文件变更 (读取/写入/编辑)                    │  │
│  │   • 工具活动 (bash/grep/edit/subagent)           │  │
│  │   • AI推理和token用量                            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              交接层 (Handoff)                        │  │
│  │                                                  │  │
│  │   • 生成结构化交接文档                           │  │
│  │   • 注入目标工具                                 │  │
│  │   • 映射通用参数                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 解析器 | `src/parsers/` | 14个工具的会话解析 | 核心 |
| 类型定义 | `src/types/` | 工具名称和类型定义 | 核心 |
| 测试 | `test-fixtures/` | 测试用例 | 质量 |
| 配置示例 | `.continues.example.yml` | 项目级配置模板 | 参考 |

## 运行与开发方式

**零安装使用**:
```bash
npx continues
```

**全局安装**:
```bash
npm install -g continues
# 提供 `continues` 和 `cont` 命令
```

**开发**:
```bash
git clone https://github.com/yigitkonur/cli-continues
cd cli-continues
pnpm install
pnpm run dev      # tsx运行，无需构建
pnpm run build    # 编译TypeScript
pnpm test         # 运行测试
```

**交互式使用**:
```bash
continues              # 启动TUI选择器
continues list         # 表格输出会话列表
continues list --json  # JSON格式
continues scan         # 发现统计
```

**快速恢复**:
```bash
continues claude        # 最新Claude会话
continues codex 3       # 第3个最新Codex会话
continues cursor        # 最新Cursor会话
```

**跨工具切换**:
```bash
# Claude rate limit后切换到Gemini
continues resume abc123 --in gemini

# 带参数传递
continues resume abc123 --in codex --yolo --search
```

**批量导出**:
```bash
continues dump all ./sessions           # 导出所有会话
continues dump claude ./sessions/claude # 仅Claude会话
continues dump all ./sessions --json    # JSON格式
```

## 外部接口

**支持的14个工具**:
| 工具 | 格式 | 会话路径 |
|------|------|----------|
| Claude Code | JSONL | ~/.claude/projects/ |
| Codex | JSONL | ~/.codex/sessions/ |
| Copilot | YAML+JSONL | ~/.copilot/session-state/ |
| Gemini CLI | JSON | ~/.gemini/tmp/*/chats/ |
| OpenCode | SQLite | ~/.local/share/opencode/storage/ |
| Cursor | JSONL | ~/.cursor/projects/*/agent-transcripts/ |
| Amp | JSON | ~/.local/share/amp/threads/ |
| Kiro | JSON | ~/Library/Application Support/Kiro/ |
| Crush | SQLite | ~/.crush/crush.db |
| Cline | JSON | VS Code globalStorage/ |
| Roo Code | JSON | VS Code globalStorage/ |
| Kilo Code | JSON | VS Code globalStorage/ |
| Factory Droid | JSONL+JSON | ~/.factory/sessions/ |
| Antigravity | JSONL | ~/.gemini/antigravity/ |

**详细度预设**:
| 预设 | 消息数 | 工具样本 | 子代理详情 | 场景 |
|------|--------|----------|------------|------|
| minimal | 3 | 0 | 无 | 快速上下文，token受限 |
| standard | 10 | 5 | 500字符 | 默认平衡 |
| verbose | 20 | 10 | 2000字符 | 调试复杂任务 |
| full | 50 | 全部 | 完整 | 完整会话捕获 |

**配置YAML** (`.continues.yml`):
```yaml
preset: verbose
recentMessages: 15
shell:
  maxSamples: 10
  stdoutLines: 20
```

**命令参考**:
| 命令 | 功能 |
|------|------|
| `continues` | 交互式TUI选择器 |
| `continues list` | 列出会话 (--source, --json, --jsonl, -n) |
| `continues resume <id>` | 按ID恢复 (--in <tool>, --preset) |
| `continues inspect <id>` | 诊断视图 |
| `continues dump <source\|all> <dir>` | 批量导出 |
| `continues scan` | 发现统计 (--rebuild) |
| `continues <tool> [n]` | 快速恢复第N个会话 |

## 数据流 / 控制流

```
扫描工具会话目录
    ↓
解析各工具原生格式
    ↓
提取消息/文件变更/工具活动
    ↓
生成结构化交接文档
    ↓
注入目标工具/生成Markdown
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| TypeScript | 主要语言 (95.7%) | 高 |
| Node.js 22+ | 运行时 (内置sqlite) | 高 |
| pnpm | 包管理 | 高 |
| Vitest | 测试 | 高 |
| Biome | 代码规范 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README | 高 |
| 上手难度 | 低 | npx直接运行 | 低 |
| 架构复杂度 | 中 | 14个解析器 | 中 |
| 外部依赖 | 低 | 只需要Node.js 22+ | 低 |
| Stars | 中 | 996 stars | 中 |
| 维护状态 | 高 | 社区活跃贡献 | 高 |

**社区贡献亮点**:
- Factory Droid支持 — #1，首个社区解析器
- Cursor AI支持 — #4 by @Evrim267
- 单工具错误处理 — #3 by @barisgirismen
- 环境变量覆盖 — #14 by @yutakobayashidev

**新增工具流程**:
1. 在 `src/parsers/` 创建解析器
2. 添加工具名到 `src/types/tool-names.ts`
3. 在 `src/parsers/registry.ts` 注册
4. 编译时完整性检查 — 添加名称但忘记解析器会抛错

**注意事项**:
- 所有读取为只读，不修改源会话文件
- 索引缓存5分钟TTL
- 支持环境变量覆盖默认路径

## 关联概念

- [[Claude-Code]] - Anthropic Claude Code
- [[Codex]] - OpenAI Codex CLI
- [[Cursor]] - Cursor AI编辑器
- [[Gemini-CLI]] - Google Gemini CLI
- [[GitHub-Copilot-CLI]] - GitHub Copilot命令行
- [[OpenCode]] - OpenCode工具
- [[Cline]] - Cline VS Code扩展
- [[Roo-Code]] - Roo Code VS Code扩展
- [[Session-Management]] - 会话管理
- [[Context-Transfer]] - 上下文迁移
- [[AI-Coding-Assistant]] - AI编码助手

---

> 来源: [GitHub](https://github.com/yigitkonur/cli-continues) | 置信度: 基于 GitHub README
> 👤 **作者**: Yigit Konur
> ⭐ **Stars**: 996
> 🔗 **官网**: [GitHub](https://github.com/yigitkonur/cli-continues)
> 📜 **许可证**: MIT
