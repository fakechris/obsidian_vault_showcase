---
title: "konsheng/Sensitive-lexicon: 中文敏感词库 (3.3k stars)"
github: "https://github.com/konsheng/Sensitive-lexicon"
owner: konsheng
repo: Sensitive-lexicon
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, sensitive-words, content-moderation, chinese, text-filtering, golang]
pinboard_tags: [security, content-moderation, chinese]
source_used: github-readme-extract
source_url: "https://github.com/konsheng/Sensitive-lexicon"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# konsheng/Sensitive-lexicon: 中文敏感词库

## 一句话概述

Sensitive-lexicon 是一个持续更新的中文敏感词库，涵盖数万条政治、色情、暴力等敏感领域词汇，提供 Go 语言检测服务，支持模糊匹配与词库热加载，方便开发者快速集成文本审核功能。

## 项目定位

**目标用户**:
- 需要内容审核功能的开发者和平台运营者
- 中文社区、论坛、社交媒体应用开发者
- 企业级内容安全团队
- 需要敏感词过滤的 SaaS 产品

**解决的问题**:
- **内容安全风险**: 用户生成内容可能包含敏感、违规信息
- **词库维护困难**: 敏感词不断变化，自建词库维护成本高
- **多语言复杂**: 中文敏感词检测需要处理变体、拼音、谐音等
- **性能需求**: 实时内容审核需要高效匹配算法

**使用场景**:
- 社交平台评论区过滤
- 直播弹幕实时审核
- 用户昵称/签名检测
- 文章/帖子发布前审核
- 即时通讯内容过滤

**与同类项目差异**:
- **中文专注**: 专门针对中文语境设计
- **社区驱动**: 定期更新，保持时效性
- **易于集成**: 纯文本格式，任意语言/框架可直接引用
- **Go 服务**: 提供原生 REST API 服务
- **模糊匹配**: 支持 N-gram 模糊匹配算法

## README 中文简介

**Sensitive-lexicon** - 持续更新的中文敏感词库

一个持续更新的中文敏感词库，帮助开发者和内容审核者快速识别并过滤不当文本。

**功能特点**:
- **广泛覆盖**: 涵盖数万条词汇，覆盖主流敏感领域
- **持续更新**: 根据社会语境变化定期更新，保持时效性与准确性
- **易于集成**: 纯文本格式，可在任意语言/框架中直接引用
- **社区驱动**: 欢迎 Issue / PR，携手打造更完整的词库

**目录结构**:
```
Sensitive-lexicon/
├── ThirdPartyCompatibleFormats/        # 用于第三方格式
├── Organized/                          # 已经进行整理的词库
├── Vocabulary/                         # 词汇库
├── LICENSE                             # 许可证
└── README.md                           # 项目说明
```

**快速开始**:
```bash
# 克隆仓库
git clone https://github.com/Konsheng/Sensitive-lexicon.git

# 在代码中读取词库 .txt 文件
# 使用 DFA、Trie、正则表达式等算法进行过滤
```

**Go 检测服务**:
提供基于 Go 的敏感词检测服务，支持模糊匹配与词库热加载。

- 服务代码路径: `./cmd/server`
- REST API: `/detect`, `/contains`, `/reload`, `/health`
- 支持分支: `dev` 开发版更频繁更新

**Docker 运行**:
```bash
docker run -p 8080:8080 ghcr.io/<您的用户名>/sensitive-lexicon-server:latest
```

**环境变量**:
- `PORT`: 服务端口
- `LEXICON_DIR`: 词库目录
- `FUZZY_MIN_NGRAM`: 模糊匹配最小 N-gram
- `FUZZY_MAX_NGRAM`: 模糊匹配最大 N-gram
- `FUZZY_MAX_DISTANCE`: 模糊匹配最大距离

**贡献词汇**:
- Pull Request: 在 `Vocabulary/` 目录新增或修改词条
- Issue: 提出建议或讨论
- PR 请附上来源或用例，便于审核

**注意事项**:
- 使用时请遵守当地法律法规及平台政策
- 敏感词定义受文化/地域/语境影响，请结合业务需求自行评估与调整

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 中文敏感词库 | 数万条政治/色情/暴力等敏感词汇 | README | 高 |
| 纯文本格式 | 任意语言/框架可直接引用 | README | 高 |
| Go 检测服务 | REST API 支持检测/重载/健康检查 | README | 高 |
| 模糊匹配 | 支持 N-gram 模糊匹配算法 | README | 高 |
| 词库热加载 | 无需重启服务更新词库 | README | 高 |
| 社区驱动 | 定期更新，PR/Issue 欢迎 | README | 高 |
| Docker 部署 | 提供容器化运行方案 | README | 高 |
| 第三方格式 | 兼容 TrChat 等第三方格式 | README | 中 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Sensitive-lexicon 架构                        │
│           (中文敏感词库与检测服务)                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              词库数据层                            │  │
│  │                                                  │  │
│  │   ├── Vocabulary/          # 原始词汇库          │  │
│  │   ├── Organized/           # 整理后的词库        │  │
│  │   └── ThirdPartyCompatibleFormats/               │  │
│  │                            # 第三方兼容格式      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              检测引擎层 (Go)                       │  │
│  │                                                  │  │
│  │   ├── DFA/Trie 算法      # 高效多模式匹配        │  │
│  │   ├── N-gram 模糊匹配    # 相似文本检测          │  │
│  │   └── 热加载机制         # 运行时更新词库        │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              REST API 层                           │  │
│  │                                                  │  │
│  │   POST /detect       # 检测文本中的敏感词        │  │
│  │   POST /contains     # 检查是否包含敏感词        │  │
│  │   POST /reload       # 重新加载词库              │  │
│  │   GET  /health       # 健康检查                  │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 原始词库 | `Vocabulary/` | 原始敏感词汇 | 数据源 |
| 整理词库 | `Organized/` | 分类整理后的词库 | 数据源 |
| 第三方格式 | `ThirdPartyCompatibleFormats/` | TrChat 等兼容格式 | 扩展 |
| Go 服务 | `cmd/server/` | REST API 检测服务 | 引擎 |

## 运行与开发方式

**快速集成**:
```bash
# 克隆仓库
git clone https://github.com/Konsheng/Sensitive-lexicon.git

# 读取词库文件
cat Sensitive-lexicon/Vocabulary/*.txt
```

**Go 服务部署**:
```bash
# 进入服务目录
cd cmd/server

# 编译运行
go build -o sensitive-server
./sensitive-server

# 或 Docker 部署
docker run -p 8080:8080 ghcr.io/<user>/sensitive-lexicon-server:latest
```

**API 调用示例**:
```bash
# 检测敏感词
curl -X POST http://localhost:8080/detect \
  -H "Content-Type: application/json" \
  -d '{"text": "测试文本"}'

# 检查是否包含敏感词
curl -X POST http://localhost:8080/contains \
  -H "Content-Type: application/json" \
  -d '{"text": "测试文本"}'

# 热重载词库
curl -X POST http://localhost:8080/reload

# 健康检查
curl http://localhost:8080/health
```

## 外部接口

**REST API**:
| 端点 | 方法 | 功能 |
|------|------|------|
| `/detect` | POST | 检测文本中的敏感词，返回匹配结果 |
| `/contains` | POST | 检查文本是否包含敏感词，返回布尔值 |
| `/reload` | POST | 重新加载词库文件 |
| `/health` | GET | 服务健康状态检查 |

**环境变量**:
| 变量 | 说明 | 默认值 |
|------|------|--------|
| `PORT` | 服务端口 | 8080 |
| `LEXICON_DIR` | 词库目录路径 | - |
| `FUZZY_MIN_NGRAM` | 模糊匹配最小 N-gram | - |
| `FUZZY_MAX_NGRAM` | 模糊匹配最大 N-gram | - |
| `FUZZY_MAX_DISTANCE` | 模糊匹配最大距离 | - |

## 数据流 / 控制流

```
用户输入文本
    ↓
检测请求 → REST API
    ↓
DFA/Trie 快速匹配
    ↓
┌────────────────┐
│ 完全匹配?      │
└────────────────┘
    ↓ 是              ↓ 否
标记敏感           N-gram 模糊匹配
    ↓                  ↓
合并结果 ←──────────────┘
    ↓
返回检测报告
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Go | 检测服务主要语言 | 高 |
| DFA/Trie | 多模式匹配算法 | 高 |
| N-gram | 模糊匹配算法 | 高 |
| Docker | 容器化部署 | 高 |
| 纯文本 | 词库存储格式 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 简洁，API 文档待完善 | 中 |
| 上手难度 | 低 | 纯文本格式，易于集成 | 低 |
| 架构复杂度 | 低 | 词库 + 检测服务 | 低 |
| 外部依赖 | 低 | 无强制依赖 | 低 |
| Stars | 中 | 3.3k stars | 中 |
| 维护状态 | 中 | 持续更新，有开发分支 | 中 |

**注意事项**:
- 使用时请遵守当地法律法规
- 敏感词定义因文化/地域/语境而异，需结合实际业务评估
- 生产环境建议配合人工审核机制
- 词库更新需考虑业务影响

## 关联概念

- [[Content-Moderation]] - 内容审核系统
- [[Text-Filtering]] - 文本过滤技术
- [[DFA-Algorithm]] - DFA 多模式匹配算法
- [[Trie-Structure]] - Trie 树数据结构
- [[N-gram-Matching]] - N-gram 模糊匹配

---

> 来源: [GitHub](https://github.com/konsheng/Sensitive-lexicon) | 置信度: 基于 GitHub README
> 👤 **作者**: konsheng
> ⭐ **Stars**: 3.3k
> 📜 **许可证**: MIT
