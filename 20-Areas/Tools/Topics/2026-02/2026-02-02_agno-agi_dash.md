---
title: "agno-agi/dash: 自学习数据智能体 (1.8k stars)"
github: "https://github.com/agno-agi/dash"
owner: agno-agi
repo: dash
date: 2026-02-02
batch_date: 2026-02-02
type: github-project
tags: [github, data-agent, sql, text-to-sql, self-learning, agno]
pinboard_tags: [agent, ai]
source_used: github-readme-extract
source_url: "https://github.com/agno-agi/dash"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# agno-agi/dash: 自学习数据智能体

## 一句话概述

Dash 是一个基于六层上下文架构的自学习数据智能体，无需重新训练或微调即可持续改进 SQL 生成质量，灵感来源于 OpenAI 内部数据智能体实现。

## 项目定位

**目标用户**:
- 需要自然语言查询数据库的数据分析师
- 希望降低 SQL 编写门槛的业务团队
- 追求 Text-to-SQL 准确性的技术负责人

**解决的问题**:
- **Schema 缺乏语义**: 原始表结构无法表达业务含义
- **类型误导**: 数据库类型与实际业务类型不一致
- **部落知识缺失**: 组织内部的业务规则和约定无法传递
- **无法从错误学习**: 传统 Text-to-SQL 重复犯同样错误
- **结果缺乏解释**: 只返回数据行，不提供洞察

**使用场景**:
- 业务人员用自然语言查询复杂数据库
- 自动学习查询错误模式并修复
- 构建可解释的数据分析助手
- 快速部署数据问答系统

**与同类项目差异**:
- **六层上下文架构**: 表使用、人工标注、查询模式、机构知识、学习成果、运行时上下文
- **自学习循环**: GPU-poor 持续学习，从错误中自动改进
- **洞察力优先**: 不只返回数据，提供可执行的洞察
- **OpenAI 灵感**: 基于 OpenAI 内部数据智能体架构

## README 中文简介

**Dash** - 自学习数据智能体，将答案建立在六层上下文之上，每次运行都能改进。

**核心理念**: 原始 LLM 写 SQL 很快遇到瓶颈——缺少上下文和记忆。Dash 用六层上下文 + 自学习循环解决。

**为什么 Text-to-SQL 在实践中失效**:
1. Schema 缺乏语义
2. 类型误导
3. 部落知识缺失
4. 无法从错误学习
5. 结果缺乏解释

**六层上下文架构**:

| 层级 | 用途 | 来源 |
|------|------|------|
| 表使用 | Schema、列、关系 | knowledge/tables/*.json |
| 人工标注 | 指标、定义、业务规则 | knowledge/business/*.json |
| 查询模式 | 已知可用的 SQL | knowledge/queries/*.sql |
| 机构知识 | 文档、wiki、外部参考 | MCP (可选) |
| 学习成果 | 错误模式和发现的修复 | Agno Learning Machine |
| 运行时上下文 | 实时 schema 变化 | introspect_schema 工具 |

**自学习循环**:
```
用户问题
    ↓
检索知识 + 学习成果
    ↓
推理意图
    ↓
生成基于上下文的 SQL
    ↓
执行并解释
    ↓
┌────┴────┐
↓         ↓
成功      错误
↓         ↓
↓         诊断 → 修复 → 保存学习成果
↓                           (永不再犯)
↓
返回洞察
    ↓
可选保存为知识
```

**快速开始**:
```bash
# 克隆仓库
git clone https://github.com/agno-agi/dash.git && cd dash

# 配置 API 密钥
cp example.env .env
# 编辑 .env 添加 OPENAI_API_KEY

# 启动应用
docker compose up -d --build

# 加载示例数据和知识
docker exec -it dash-api python -m dash.scripts.load_data
docker exec -it dash-api python -m dash.scripts.load_knowledge
```

**访问**: http://localhost:8000/docs

**Web UI**: 打开 os.agno.com → Add OS → Local → http://localhost:8000

**示例查询** (F1 数据集):
- "Who won the most F1 World Championships?"
- "How many races has Lewis Hamilton won?"
- "Compare Ferrari vs Mercedes points 2015-2020"

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 六层上下文 | 表使用、标注、模式、知识、学习、运行时 | README | 高 |
| 自学习 | 从错误中自动学习，无需重新训练 | README | 高 |
| 混合搜索 | 查询时检索相关上下文 | README | 高 |
| 洞察生成 | 不只返回数据，提供可执行洞察 | README | 高 |
| Railway 部署 | 一键部署到 Railway | README | 高 |
| Agno 生态 | 属于 Agno (原 Phidata) 生态系统 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│                  Dash 系统架构                             │
│           (自学习数据智能体)                                │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              用户交互层                          │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │   Web UI     │    │   API Docs   │        │  │
│  │   │  os.agno.com │    │ localhost:8000/docs   │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              智能体核心层                         │  │
│  │                                                  │  │
│  │   ┌────────────────────────────────────────┐   │  │
│  │   │           Dash Agent                  │   │  │
│  │   │                                          │   │  │
│  │   │  • 意图推理                               │   │  │
│  │   │  • 上下文检索 (混合搜索)                 │   │  │
│  │   │  • SQL 生成                               │   │  │
│  │   │  • 结果解释                               │   │  │
│  │   │                                          │   │  │
│  │   │  知识来源 ──▶ knowledge/               │   │  │
│  │   │  学习成果 ──▶ Agno Learning Machine    │   │  │
│  │   │                                          │   │  │
│  │   └────────────────────────────────────────┘   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              知识管理层                          │  │
│  │                                                  │  │
│  │   knowledge/                                     │  │
│  │   ├── tables/      # 表元数据和注意事项          │  │
│  │   ├── queries/     # 已验证的 SQL 模式          │  │
│  │   └── business/    # 指标和业务语言             │  │
│  │                                                  │  │
│  │   Agno Learning Machine ──▶ 错误模式学习        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              数据层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │   dash-db    │    │  外部数据源  │        │  │
│  │   │  (PostgreSQL)│    │  (可配置)    │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              外部服务层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┐    ┌──────────────┐        │  │
│  │   │   OpenAI     │    │    Exa       │        │  │
│  │   │   API        │    │  (搜索)      │        │  │
│  │   └──────────────┘    └──────────────┘        │  │
│  │                                                  │  │
│  │   环境变量: OPENAI_API_KEY, EXA_API_KEY        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 应用入口 | `app/` | FastAPI Web 应用 | 用户接口 |
| 智能体核心 | `dash/` | Agent 逻辑 | 核心引擎 |
| 脚本工具 | `scripts/` | 数据加载、部署 | 辅助工具 |
| 知识库 | `knowledge/` | 表定义、查询、业务规则 | 上下文源 |
| 数据库 | `db/` | PostgreSQL 相关 | 数据存储 |
| 示例数据 | `dash/scripts/load_data` | 数据初始化 | 演示 |

## 运行与开发方式

**快速开始**:
```bash
# 克隆
git clone https://github.com/agno-agi/dash.git && cd dash

# 配置 API 密钥
cp example.env .env
# 编辑 .env: OPENAI_API_KEY=your_key

# 启动
docker compose up -d --build

# 加载数据
docker exec -it dash-api python -m dash.scripts.load_data
docker exec -it dash-api python -m dash.scripts.load_knowledge
```

**本地开发**:
```bash
./scripts/venv_setup.sh && source .venv/bin/activate
docker compose up -d dash-db
python -m dash.scripts.load_data
python -m dash  # CLI 模式
```

**Railway 部署**:
```bash
railway login
./scripts/railway_up.sh

# 生产数据加载
railway run python -m dash.scripts.load_data
railway run python -m dash.scripts.load_knowledge
```

**添加知识**:
```bash
python -m dash.scripts.load_knowledge            # 增量更新
python -m dash.scripts.load_knowledge --recreate # 全新开始
```

**环境变量**:
| 变量 | 必需 | 说明 |
|------|------|------|
| OPENAI_API_KEY | 是 | OpenAI API 密钥 |
| EXA_API_KEY | 否 | Web 搜索外部知识 |
| DB_* | 否 | 数据库配置 (默认 localhost) |

## 外部接口

**API 端点**:
| 地址 | 功能 |
|------|------|
| http://localhost:8000/docs | API 文档 (Swagger) |
| http://localhost:8000 | 应用入口 |

**Web UI**:
- 地址: https://os.agno.com
- 连接: Add OS → Local → http://localhost:8000

**知识库结构**:
```
knowledge/
├── tables/      # 表元数据 (JSON)
├── queries/     # 查询模式 (SQL)
└── business/    # 业务规则 (JSON)
```

**CLI 命令**:
```bash
python -m dash              # CLI 交互模式
python -m dash.scripts.load_data      # 加载数据
python -m dash.scripts.load_knowledge   # 加载知识
```

## 数据流 / 控制流

```
用户自然语言查询
    ↓
┌────────────────────────────────────────────────────────────┐
│ 1. 检索相关上下文                                           │
│    • 表使用信息 (knowledge/tables/)                        │
│    • 人工标注 (knowledge/business/)                        │
│    • 查询模式 (knowledge/queries/)                         │
│    • 学习成果 (Agno Learning Machine)                      │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 2. 推理意图                                                 │
│    • 理解用户真实问题意图                                   │
│    • 匹配已知查询模式                                     │
│    • 应用学习成果避免历史错误                             │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 3. 生成基于上下文的 SQL                                     │
│    • 使用已验证的查询模式                                 │
│    • 应用业务规则和指标定义                               │
│    • 考虑数据质量注意事项                                 │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 4. 执行与解释                                              │
│    • 执行生成的 SQL                                       │
│    • 解释结果的业务含义                                   │
│    • 生成可执行的洞察                                     │
└────────────────────────────────────────────────────────────┘
    ↓
┌────────────────────────────────────────────────────────────┐
│ 5. 学习与改进                                              │
│    ├── 成功: 可选保存为知识                               │
│    └── 错误: 诊断 → 修复 → 保存学习成果 (永不重复)       │
└────────────────────────────────────────────────────────────┘
    ↓
返回给用户: 洞察 (不只是数据行)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 核心语言 | 高 |
| FastAPI | Web 框架 | 高 |
| PostgreSQL | 数据库 | 高 |
| Docker | 部署 | 高 |
| OpenAI API | LLM 能力 | 高 |
| Railway | 云部署 | 高 |
| Agno Framework | Agent 框架 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | README 详细，架构清晰 | 高 |
| 上手难度 | 低 | Docker Compose 一键启动 | 低 |
| 架构复杂度 | 高 | 六层上下文 + 自学习 | 高 |
| 外部依赖 | 中 | 依赖 OpenAI API | 中 |
| Stars | 中 | 1.8k stars |
| 生态整合 | 高 | Agno 官方项目 | 高 |

**注意事项**:
- 需要 OpenAI API 密钥
- 知识库需要持续维护才能达到最佳效果
- 学习成果需要一定时间积累
- 复杂查询可能需要人工验证

## 关联概念

- [[Text-to-SQL]] - 自然语言转 SQL
- [[Data-Agent]] - 数据智能体
- [[Agno]] - Agno Agent 框架 (原 Phidata)
- [[Self-Learning]] - 自学习系统
- [[Context-Engineering]] - 上下文工程
- [[LLM-SQL]] - LLM 生成 SQL

---

> 来源: [GitHub](https://github.com/agno-agi/dash) | 置信度: 基于 GitHub README
> 👤 **作者**: agno-agi (Agno 团队)
> ⭐ **Stars**: 1.8k
> 🔗 **关联**: [OpenAI 内部数据智能体](https://openai.com/index/making-models-smarter-with-data-agents/)
