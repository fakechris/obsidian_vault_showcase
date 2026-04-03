---
title: "langchain-ai/langchain: LLM 应用开发框架 (132k stars)"
github: "https://github.com/langchain-ai/langchain"
owner: langchain-ai
repo: langchain
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, python, llm, ai-framework, langchain, agents, rag]
pinboard_tags: [ai-framework, llm, python]
source_used: github-readme-extract
source_url: "https://github.com/langchain-ai/langchain"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# langchain-ai/langchain: LLM 应用开发框架

## 一句话概述

LangChain 是一个用于构建 Agent 和 LLM 驱动应用的框架，通过链式组合可互操作的组件和第三方集成来简化 AI 应用开发，支持模型互操作性、RAG 数据增强、Agent 工作流编排和 LangSmith 可观测性，是应用工程化的平台。

## 项目定位

**目标用户**:
- 构建 LLM 驱动应用的开发者
- AI Agent 和 RAG 系统开发者
- 需要集成多个模型和工具的团队
- 寻求生产级 AI 解决方案的工程师

**解决的问题**:
- **模型碎片化**: 不同提供商的 API 差异大，切换成本高
- **数据上下文**: LLM 缺乏实时和专有数据
- **复杂工作流**: 简单调用无法满足多步骤 Agent 需求
- **生产可靠性**: 缺乏监控、调试和评估工具
- **快速原型**: 从零搭建 LLM 应用周期长

**使用场景**:
- 对话式 AI 助手
- RAG 知识库问答
- 多步骤 Agent 任务执行
- 自动化工作流编排
- LLM 应用评估和监控

**与同类项目差异**:
- **组件化架构**: 模块化设计，灵活组合
- **生态丰富**: LangSmith、LangGraph、Deep Agents 完整产品矩阵
- **模型中立**: 支持 OpenAI、Anthropic、Gemini 等任意模型
- **生产就绪**: 内置监控、评估、调试能力
- **活跃社区**: 大量集成和模板，持续更新

## README 中文简介

**LangChain** - Agent 工程平台

LangChain 是一个用于构建 Agent 和 LLM 驱动应用的框架。它帮助您将可互操作的组件和第三方集成链接在一起，简化 AI 应用开发 —— 同时在底层技术演进时保护您的决策。

**快速开始**:
```bash
pip install langchain
# 或
uv add langchain
```

```python
from langchain.chat_models import init_chat_model

model = init_chat_model("openai:gpt-5.4")
result = model.invoke("Hello, world!")
```

如果您需要更高级的定制或 Agent 编排，请查看 [LangGraph](https://github.com/langchain-ai/langgraph)，我们用于构建可控 Agent 工作流的框架。

**开发调试部署**: 参见 [LangSmith](https://smith.langchain.com)。

**LangChain 生态系统**:

虽然 LangChain 框架可以独立使用，但它也与所有 LangChain 产品无缝集成，为开发者提供构建 LLM 应用的完整工具套件。

| 产品 | 功能 |
|------|------|
| [Deep Agents](https://github.com/langchain-ai/deepagents) | 构建能规划、使用子 Agent、利用文件系统处理复杂任务的 Agent |
| [LangGraph](https://github.com/langchain-ai/langgraph) | 构建能可靠处理复杂任务的可控 Agent 工作流 |
| [Integrations](https://python.langchain.com/docs/integrations) | 聊天与嵌入模型、工具与工具包等 |
| [LangSmith](https://smith.langchain.com) | Agent 评估、可观测性和 LLM 应用调试 |
| [LangSmith Deployment](https://langchain.com/deployment) | 为长时间运行、有状态工作流构建的专用部署平台 |

**为什么使用 LangChain?**

LangChain 帮助开发者通过为模型、嵌入、向量存储等提供标准接口来构建 LLM 驱动的应用。

- **实时数据增强** — 轻松将 LLM 连接到各种数据源和外部/内部系统，从 LangChain 丰富的集成库中汲取资源
- **模型互操作性** — 在工程团队实验以找到最适合应用需求的模型时，自由切换模型
- **快速原型** — 使用 LangChain 的模块化、基于组件的架构快速构建和迭代 LLM 应用
- **生产就绪功能** — 通过与 LangSmith 等集成，使用内置的监控、评估和调试支持部署可靠应用
- **活跃社区和生态** — 利用丰富的集成、模板和社区贡献组件生态
- **灵活抽象层** — 在适合您需求的抽象级别上工作

**文档**:

- [docs.langchain.com](https://python.langchain.com) — 综合文档，包括概念概述和指南
- [reference.langchain.com/python](https://api.python.langchain.com) — LangChain 包的 API 参考
- [Chat LangChain](https://chat.langchain.com) — 与 LangChain 文档对话，获取问题答案
- [LangChain Forum](https://discuss.langchain.com) — 社区讨论

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 模型接口 | 统一接口支持多种 LLM | README | 高 |
| 链式组件 | 模块化组件组合 | README | 高 |
| RAG 支持 | 检索增强生成 | README | 高 |
| Agent 编排 | 可控 Agent 工作流 | README | 高 |
| 工具集成 | 丰富的第三方集成 | README | 高 |
| 向量存储 | 多种向量数据库支持 | README | 高 |
| 嵌入模型 | 多提供商嵌入接口 | README | 高 |
| 可观测性 | LangSmith 监控调试 | README | 高 |
| 评估测试 | 应用评估框架 | README | 高 |
| 生产部署 | LangSmith Deployment 支持 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              LangChain 架构                                │
│           (LLM 应用开发框架)                               │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              模型接口层                              │  │
│  │                                                  │  │
│  │   ┌──────────┬──────────┬──────────┬──────────┐  │  │
│  │   │ OpenAI   │Anthropic │  Gemini  │  Azure   │  │  │
│  │   ├──────────┼──────────┼──────────┼──────────┤  │  │
│  │   │  Ollama  │ Mistral  │  Cohere  │  更多...  │  │  │
│  │   └──────────┴──────────┴──────────┴──────────┘  │  │
│  │                                                  │  │
│  │   统一接口: Chat Models / LLMs / Embeddings    │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              组件层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │   Prompts    │   Chains     │   Agents     ││  │
│  │   │   (提示模板)   │   (链式调用)  │   (智能体)   ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │  Document    │  Text Split  │  VectorStore ││  │
│  │   │  Loaders     │  (文本分割)   │  (向量存储)   ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │   Tools      │  Callbacks   │   Memory     ││  │
│  │   │   (工具调用)  │   (回调机制)   │   (记忆)      ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │    RAG       │   Agent      │   Chatbot    ││  │
│  │   │   (知识库)    │   (任务执行)  │   (对话机器人) ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │  Extraction  │   QA         │  Summarizer  ││  │
│  │   │   (信息提取)  │   (问答)      │   (摘要生成)  ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              生态产品                              │  │
│  │                                                  │  │
│  │   LangGraph → Agent 工作流编排                     │  │
│  │   LangSmith → 监控、评估、调试                     │  │
│  │   Deep Agents → 复杂任务规划                       │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心库 | `libs/langchain/` | 框架核心 | 核心 |
| 社区集成 | `libs/community/` | 第三方集成 | 核心 |
| 合作伙伴 | `libs/partners/` | 官方合作包 | 扩展 |
| 文本分割 | `libs/text-splitters/` | 文本分割 | 工具 |
| 标准测试 | `libs/standard-tests/` | 测试套件 | 质量 |

## 运行与开发方式

**快速开始**:

**安装**:
```bash
pip install langchain
# 或
uv add langchain
```

**基础用法**:
```python
from langchain.chat_models import init_chat_model

# 初始化模型
model = init_chat_model("openai:gpt-5.4")
result = model.invoke("Hello, world!")
print(result)
```

**RAG 示例**:
```python
from langchain.document_loaders import WebBaseLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain.vectorstores import Chroma
from langchain.embeddings import OpenAIEmbeddings
from langchain.chains import RetrievalQA

# 加载文档
loader = WebBaseLoader("https://example.com/doc")
docs = loader.load()

# 分割文本
splitter = RecursiveCharacterTextSplitter()
chunks = splitter.split_documents(docs)

# 创建向量存储
vectorstore = Chroma.from_documents(chunks, OpenAIEmbeddings())

# 创建 RAG 链
qa = RetrievalQA.from_chain_type(
    llm=init_chat_model("openai:gpt-5.4"),
    retriever=vectorstore.as_retriever()
)
```

**Agent 示例**:
```python
from langchain.agents import AgentExecutor, create_openai_tools_agent
from langchain.tools import Tool

# 定义工具
tools = [
    Tool(
        name="Search",
        func=search_function,
        description="Search for information"
    )
]

# 创建 Agent
agent = create_openai_tools_agent(
    llm=init_chat_model("openai:gpt-5.4"),
    tools=tools,
    prompt=prompt
)

# 执行
agent_executor = AgentExecutor(agent=agent, tools=tools)
result = agent_executor.invoke({"input": "Find the weather in NYC"})
```

**开发贡献**:
```bash
# 克隆仓库
git clone https://github.com/langchain-ai/langchain.git
cd langchain

# 安装依赖
pip install -e libs/langchain

# 运行测试
pytest libs/langchain/tests/
```

## 外部接口

**核心 API**:
| 类/函数 | 功能 |
|---------|------|
| `init_chat_model()` | 初始化聊天模型 |
| `ChatOpenAI` | OpenAI 聊天模型 |
| `ChatAnthropic` | Anthropic 聊天模型 |
| `OpenAIEmbeddings` | OpenAI 嵌入 |
| `Chroma` | Chroma 向量存储 |
| `RecursiveCharacterTextSplitter` | 递归文本分割 |
| `WebBaseLoader` | 网页加载器 |
| `RetrievalQA` | RAG 问答链 |
| `AgentExecutor` | Agent 执行器 |

**LCEL (LangChain Expression Language)**:
```python
from langchain_core.runnables import RunnablePassthrough
from operator import itemgetter

chain = (
    {"context": retriever, "question": RunnablePassthrough()}
    | prompt
    | model
    | parser
)
```

**集成列表**:
- 模型: OpenAI, Anthropic, Google, Azure, Ollama, Mistral, Cohere...
- 向量存储: Chroma, Pinecone, Weaviate, Milvus, Qdrant...
- 文档加载: Web, PDF, Notion, Confluence, GitHub...
- 工具: Google Search, Wikipedia, SQL, API...

## 数据流 / 控制流

```
用户输入
    ↓
┌────────────────────────────────┐
│ 数据加载 (Document Loaders)     │
│ • Web, PDF, Database...         │
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ 文本分割 (Text Splitters)       │
│ • Chunk 化处理                  │
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ 嵌入生成 (Embeddings)           │
│ • 向量化                        │
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ 向量存储 (Vector Store)           │
│ • 索引和检索                    │
└──────────────┬─────────────────┘
               ↓
用户查询 → 相似性搜索 → 相关文档
               ↓
┌────────────────────────────────┐
│ 提示构建 (Prompt Template)      │
│ • 组合上下文和问题              │
└──────────────┬─────────────────┘
               ↓
┌────────────────────────────────┐
│ LLM 调用                        │
│ • 生成回答                      │
└──────────────┬─────────────────┘
               ↓
           输出结果
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (99.3%) | 高 |
| Pydantic | 数据验证 | 高 |
| Pytest | 测试框架 | 高 |
| OpenAI API | 模型集成 | 高 |
| Chroma/Pinecone | 向量存储 | 高 |
| LangSmith | 可观测性 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详尽文档、API 参考、教程丰富 | 高 |
| 上手难度 | 中 | 概念较多，有学习曲线 | 中 |
| 架构复杂度 | 中 | 模块化但组件众多 | 中 |
| 外部依赖 | 中 | 依赖模型 API 和第三方服务 | 中 |
| Stars | 高 | 132k stars | 高 |
| 维护状态 | 高 | 活跃开发，1,192 releases | 高 |
| 使用量 | 极高 | 278k+ 项目使用 | 极高 |

**生态产品**:
- **LangGraph**: Agent 工作流编排框架
- **LangSmith**: 监控、评估、调试平台
- **Deep Agents**: 复杂任务规划 Agent
- **LangChain.js**: JavaScript/TypeScript 版本
- **LangChain Academy**: 官方免费课程

**注意事项**:
- API 变化较快，关注版本更新
- 生产环境建议使用 LangSmith 监控
- 复杂 Agent 推荐使用 LangGraph
- 注意 API 调用成本和速率限制

## 关联概念

- [[LLM]] - 大语言模型
- [[RAG]] - 检索增强生成
- [[Agent]] - 智能体
- [[Prompt-Engineering]] - 提示工程
- [[Vector-Store]] - 向量存储
- [[Embeddings]] - 嵌入向量
- [[LangGraph]] - 工作流编排
- [[LangSmith]] - LLM 可观测性

---

> 来源: [GitHub](https://github.com/langchain-ai/langchain) | 置信度: 基于 GitHub README
> 👤 **作者**: LangChain Inc. (Harrison Chase 等)
> ⭐ **Stars**: 132k
> 🔗 **官网**: [langchain.com](https://langchain.com)
> 📚 **文档**: [python.langchain.com](https://python.langchain.com)
> 📜 **许可证**: MIT
