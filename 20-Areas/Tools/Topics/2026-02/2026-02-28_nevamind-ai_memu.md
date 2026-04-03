---
title: "NevaMind-AI/memU: 24/7主动式AI记忆框架 (13.3k stars)"
github: "https://github.com/NevaMind-AI/memU"
owner: NevaMind-AI
repo: memU
date: 2026-02-28
batch_date: 2026-02-28
type: github-project
tags: [github, python, ai, memory, agent, proactive, openclaw]
pinboard_tags: [agent, memory, openclaw]
source_used: github-readme-extract
source_url: "https://github.com/NevaMind-AI/memU"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# NevaMind-AI/memU: 24/7主动式AI记忆框架

## 一句话概述

memU是为24/7全天候主动式Agent设计的记忆框架，通过分层记忆架构和连续学习管道，大幅降低长时运行Agent的LLM Token成本，实现真正的永远在线、自我进化的生产级Agent系统。

## 项目定位

**目标用户**:
- 构建7×24小时主动式AI Agent的开发者
- 需要长期记忆和上下文保持的Agent团队
- 寻求降低LLM调用成本的AI应用架构师
- 需要意图预测和主动响应能力的Agent开发者

**解决的问题**:
- **Token成本过高**: 长时运行Agent需要大量上下文Token
- **记忆碎片化**: 会话间上下文丢失，每次从零开始
- **被动响应**: Agent只能响应查询，无法主动行动
- **意图理解困难**: 无法从交互中自动学习用户意图
- **缺乏预见性**: 无法预测用户需求并提前准备

**使用场景**:
- 24/7个人AI助手（如Clawdbot替代方案）
- 主动信息推荐系统
- 智能邮件管理和自动回复
- 交易监控和财务助理
- 客服Agent的记忆增强

**与同类项目差异**:
- **主动式记忆**: 不仅存储，还能预测用户意图并主动行动
- **分层架构**: Resource-Item-Category三层，支持反应式和主动式使用
- **文件系统映射**: 记忆如同文件系统，可导航、可挂载、可交叉引用
- **成本优化**: 通过缓存和避免冗余LLM调用降低Token成本约90%
- **连续学习**: 实时处理输入，立即更新记忆，零延迟

## README 中文简介

**memU** — 24/7 Always-On Proactive Memory for AI Agents

为长时运行Agent设计的记忆框架，大幅降低保持Agent永远在线的LLM Token成本，使生产级始终在线、自我进化的Agent成为可能。

**核心特性**:
- **24/7主动式Agent**: 始终在后台连续工作，永不休眠，永不遗忘
- **用户意图捕获**: 跨会话自动理解和记忆用户目标、偏好和上下文
- **成本高效**: 通过缓存洞察和避免冗余LLM调用降低长时运行Token成本
- **连续学习管道**: 实时处理，立即更新，零延迟可用
- **文件系统式记忆**: 结构化、分层、即时访问，如同浏览目录

**分层记忆架构**:
| 层级 | 反应式使用 | 主动式使用 | 对应文件系统 |
|------|-----------|-----------|-------------|
| Resource | 原始数据直接访问 | 后台监控新模式 | 📁 文件夹 |
| Item | 针对性事实检索 | 实时从持续交互提取 | 📄 文件 |
| Category | 摘要级概览 | 自动组装预期上下文 | 🏷️ 分类 |

**主动式用例**:
1. **信息推荐**: 监控兴趣，主动推荐相关内容
2. **邮件管理**: 学习通信模式，自动处理日常邮件
3. **交易监控**: 跟踪市场上下文和投资行为，主动预警

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 24/7连续学习 | 实时处理输入，立即更新记忆 | README | 高 |
| 意图预测 | 预测用户下一步需求和行动 | README | 高 |
| RAG检索 | 毫秒级基于嵌入的上下文组装 | README | 高 |
| LLM检索 | 深度推理的复杂上下文理解 | README | 高 |
| 分层架构 | Resource-Item-Category三层记忆 | README | 高 |
| 自动分类 | 无需手动标签的自组织主题 | README | 高 |
| 交叉引用 | 记忆相互关联，构建知识图谱 | README | 高 |
| 成本优化 | ~1/10的Token成本（相比同等使用） | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              memU 架构                                     │
│           (24/7主动式AI记忆框架)                             │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ 个人助手     │ 邮件管理     │ 交易监控     ││  │
│  │   │ (memUBot)    │ (自动化)     │ (预警)       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              主动式记忆层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ 🤖 Main      │ 🧠 memU      │              │  │
│  │   │ Agent        │ Bot          │              │  │
│  │   │ (处理查询)   │ (监控&记忆)  │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              核心引擎层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ memorize()   │ retrieve()   │ 意图预测     ││  │
│  │   │ (连续学习)   │ (双模式检索) │ (主动)       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              记忆存储层                            │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Resource     │ Item         │ Category     ││  │
│  │   │ (原始数据)   │ (记忆项)     │ (分类)       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心引擎 | `src/` | memorize/retrieve/意图预测 | 核心 |
| 示例 | `examples/` | 主动式用例演示 | 参考 |
| 测试 | `tests/` | 内存/PostgreSQL测试 | 质量 |
| 文档 | `docs/` | API文档和集成指南 | 文档 |
| memUBot | 独立仓库 | 企业级OpenClaw替代 | 应用 |

## 运行与开发方式

**快速开始 - Cloud版本**:
- 体验地址: https://memu.so
- API文档: https://api.memu.so
- 企业部署: info@nevamind.ai

**本地安装**:
```bash
pip install -e .
```

**基础示例** (Python 3.13+, OpenAI API Key):
```bash
export OPENAI_API_KEY=your_api_key
cd tests
python test_inmemory.py        # 内存存储测试
python test_postgres.py        # PostgreSQL持久化测试
```

**核心API使用**:

```python
from memu import MemUService

# 初始化服务
service = MemUService()

# 连续学习 - 实时处理并更新记忆
result = await service.memorize(
    resource_url="path/to/file.json",
    modality="conversation",  # conversation | document | image
    user={"user_id": "123"}
)
# 返回: resource, items (即时可用), categories

# 检索 - 双模式支持
# RAG模式 (快速上下文组装)
result = await service.retrieve(
    queries=[{"role": "user", "content": {"text": "查询"}}],
    where={"user_id": "123"},
    method="rag"  # 或 "llm" 深度推理
)
# 返回: categories, items, resources, next_step_query
```

**自定义LLM配置**:
```python
service = MemUService(
    llm_profiles={
        "default": {
            "base_url": "https://dashscope.aliyuncs.com/compatible-mode/v1",
            "api_key": "your_key",
            "chat_model": "qwen3-max",
            "client_backend": "sdk"
        },
        "embedding": {
            "base_url": "https://api.voyageai.com/v1",
            "api_key": "your_key",
            "embed_model": "voyage-3.5-lite"
        }
    }
)
```

**OpenRouter集成**:
```python
service = MemoryService(
    llm_profiles={
        "default": {
            "provider": "openrouter",
            "client_backend": "httpx",
            "base_url": "https://openrouter.ai",
            "api_key": "your_key",
            "chat_model": "anthropic/claude-3.5-sonnet",
            "embed_model": "openai/text-embedding-3-small"
        }
    }
)
```

## 外部接口

**Cloud API v3**:
| 方法 | 端点 | 描述 |
|------|------|------|
| POST | `/api/v3/memory/memorize` | 注册连续学习任务 |
| GET | `/api/v3/memory/memorize/status/{task_id}` | 检查实时处理状态 |
| POST | `/api/v3/memory/categories` | 列出自动生成分类 |
| POST | `/api/v3/memory/retrieve` | 查询记忆（支持主动上下文加载）|

**memorize() 参数**:
| 参数 | 说明 |
|------|------|
| `resource_url` | 文件路径或URL |
| `modality` | conversation/document/image/video/audio |
| `user` | 可选用户范围 |

**retrieve() 参数**:
| 参数 | 说明 |
|------|------|
| `queries` | 查询列表（支持上下文历史）|
| `where` | 范围过滤 (user_id, agent_id等) |
| `method` | "rag" (快速) 或 "llm" (深度推理) |

**检索方法对比**:
| 特性 | RAG (快速上下文) | LLM (深度推理) |
|------|-----------------|----------------|
| 速度 | 毫秒级 | 秒级 |
| 成本 | 仅嵌入成本 | LLM推理成本 |
| 主动使用 | 连续监控 | 触发式上下文加载 |
| 最佳场景 | 实时建议 | 复杂预期 |

## 数据流 / 控制流

```
用户输入/Agent交互
    ↓
memorize() 连续学习管道
    ↓
实时提取记忆项 → 自动分类 → 交叉引用现有记忆
    ↓
记忆立即可用 (零延迟)
    ↓
retrieve() 检索 (RAG快速 或 LLM深度)
    ↓
意图预测 → 主动任务执行
    ↓
持续同步循环 (Agent ◄──► memU Bot ◄──► DB)
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (99.8%) | 高 |
| OpenAI API | 默认LLM后端 | 高 |
| PostgreSQL + pgvector | 持久化存储 | 高 |
| Embedding | 向量检索 | 高 |
| RAG | 快速上下文组装 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，多语言支持 | 高 |
| 上手难度 | 中 | 需要Python 3.13+和API Key | 中 |
| 架构复杂度 | 高 | 分层记忆 + 主动式管道 | 高 |
| 外部依赖 | 中 | 需要LLM和Embedding API | 中 |
| Stars | 高 | 13.3k stars | 高 |
| 维护状态 | 高 | 活跃开发，24个Release | 高 |

**性能指标**:
- Locomo基准测试: 92.09% 平均准确率
- Token成本: ~1/10 (相比同等使用)
- RAG检索: 毫秒级

**注意事项**:
- 主动式功能需要精心设计避免过度打扰用户
- 记忆隐私和安全需要额外考虑
- 意图预测准确性依赖训练数据质量

## 关联概念

- [[OpenClaw]] - AI Agent框架
- [[Clawdbot]] - memU Bot的对标产品
- [[Moltbot]] - 另一个相关Agent
- [[RAG]] - Retrieval-Augmented Generation
- [[Vector-Database]] - 向量数据库
- [[Proactive-AI]] - 主动式AI
- [[Agent-Memory]] - Agent记忆系统
- [[LLM-Cost-Optimization]] - LLM成本优化
- [[PostgreSQL]] - 关系数据库
- [[pgvector]] - PostgreSQL向量扩展

---

> 来源: [GitHub](https://github.com/NevaMind-AI/memU) | 置信度: 基于 GitHub README
> 👤 **作者**: NevaMind-AI
> ⭐ **Stars**: 13.3k
> 🔗 **官网**: [memu.pro](https://memu.pro) | [memu.so](https://memu.so)
> 📜 **许可证**: Apache License 2.0
