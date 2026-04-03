---
title: "ZhuLinsen/daily_stock_analysis: LLM驱动股票智能分析系统 (27.8k stars)"
github: "https://github.com/ZhuLinsen/daily_stock_analysis"
owner: ZhuLinsen
repo: daily_stock_analysis
date: 2026-02-26
batch_date: 2026-02-26
type: github-project
tags: [github, python, ai, stock, trading, gemini, llm, analysis]
pinboard_tags: [stock, ai, trading]
source_used: github-readme-extract
source_url: "https://github.com/ZhuLinsen/daily_stock_analysis"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# ZhuLinsen/daily_stock_analysis: LLM驱动股票智能分析系统

## 一句话概述

基于AI大模型的A股/港股/美股自选股智能分析系统，每日自动分析并推送「决策仪表盘」到企业微信/飞书/Discord等渠道，支持技术面、筹码分布、舆情情报、实时行情多维度分析。

## 项目定位

**目标用户**:
- 需要AI辅助股票分析的散户投资者
- 希望自动化盯盘和报告推送的交易者
- 需要多市场(A股/港股/美股)数据的专业投资者
- 寻求AI决策仪表盘和精确买卖点位的用户

**解决的问题**:
- **信息过载**: 市场数据、新闻、舆情难以整合
- **分析门槛高**: 技术面和基本面分析需要专业知识
- **实时性不足**: 无法及时获取市场变化信号
- **多平台切换**: 需要在多个APP间切换查看信息

**使用场景**:
- 每日自动股票分析和推送
- 多市场(A/港/美)投资组合监控
- 技术面+基本面综合决策支持
- 历史回测验证AI预测准确率
- AI问股和策略对话

**与同类项目差异**:
- **决策仪表盘**: 一句话核心结论 + 精确买卖点位 + 操作检查清单
- **多数据源**: AkShare/Tushare/Longbridge/YFinance等
- **多LLM支持**: Gemini/Claude/OpenAI/DeepSeek/Ollama
- **零成本部署**: GitHub Actions定时执行，无需服务器
- **多渠道推送**: 企业微信/飞书/Discord/Telegram/Slack等

## README 中文简介

**📈 股票智能分析系统**

基于 AI 大模型的 A股/港股/美股自选股智能分析系统，每日自动分析并推送「决策仪表盘」到企业微信/飞书/Telegram/Discord/Slack/邮箱。

**核心特性**:
| 模块 | 功能 | 说明 |
|------|------|------|
| AI决策 | 决策仪表盘 | 一句话核心结论 + 精确买卖点位 + 操作检查清单 |
| 分析 | 多维度分析 | 技术面(MA/多头排列) + 筹码分布 + 舆情情报 + 实时行情 |
| 市场 | 全球市场 | 支持 A股、港股、美股及美股指数(SPX/DJI/IXIC) |
| 基本面 | 结构化聚合 | 估值/增长/盈利/机构/资金流向/龙虎榜 |
| 策略 | 市场策略系统 | A股「三段式复盘」与美股「Regime Strategy」|
| 复盘 | 大盘复盘 | 每日市场概览、板块涨跌 |
| 推送 | 多渠道通知 | 企业微信、飞书、Telegram、Discord等 |
| 自动化 | 定时运行 | GitHub Actions定时执行，无需服务器 |

**内置交易纪律**:
- 严禁追高: 乖离率超阈值自动提示风险
- 趋势交易: MA5 > MA10 > MA20 多头排列
- 精确点位: 买入价、止损价、目标价
- 检查清单: 每项条件标记「满足/注意/不满足」

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| AI决策仪表盘 | 一句话结论+精确点位+检查清单 | README | 高 |
| 多维度分析 | 技术面+筹码+舆情+行情 | README | 高 |
| 多市场支持 | A股/港股/美股/指数 | README | 高 |
| 基本面聚合 | 估值/增长/盈利/机构/资金流向 | README | 高 |
| 多LLM支持 | Gemini/Claude/OpenAI/DeepSeek/Ollama | README | 高 |
| 智能导入 | 图片/CSV/剪贴板多源导入 | README | 高 |
| AI回测验证 | 历史分析准确率评估 | README | 高 |
| 多渠道推送 | 企业微信/飞书/Discord等 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              daily_stock_analysis 架构                     │
│           (LLM驱动股票智能分析系统)                         │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              推送层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ 企业微信     │ 飞书         │ Discord      ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ Telegram     │ Slack        │ 邮件/其他    ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              分析引擎层                              │  │
│  │                                                  │  │
│  │   • AI决策仪表盘生成                             │  │
│  │   • 技术面分析 (MA/多头排列)                     │  │
│  │   • 筹码分布分析                                 │  │
│  │   • 舆情情报聚合                                 │  │
│  │   • 基本面聚合                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              数据层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ AkShare      │ Tushare      │ Longbridge   ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ YFinance     │ Pytdx        │ Baostock     ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              LLM层                                 │  │
│  │                                                  │  │
│  │   • Gemini (推荐)                                │  │
│  │   • Claude (Anthropic)                         │  │
│  │   • OpenAI兼容 (DeepSeek/通义千问)             │  │
│  │   • Ollama本地模型                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录/文件 | 职责 | 关系 |
|------|----------|------|------|
| 主程序 | `main.py` | 分析主入口 | 核心 |
| 分析服务 | `analyzer_service.py` | AI分析服务 | 核心 |
| Web界面 | `webui.py` | 双主题工作台 | 接口 |
| 数据源 | `data_provider/` | 多数据源适配 | 核心 |
| 策略 | `strategies/` | 三段式复盘/Regime | 核心 |
| Bot | `bot/` | Telegram/Discord Bot | 接口 |
| Skill定义 | `SKILL.md` | AI工具集成 | 扩展 |

## 运行与开发方式

**快速开始 - GitHub Actions (推荐，零成本)**:

1. **Fork仓库** 并点击Star⭐

2. **配置Secrets** (Settings → Secrets → Actions):

   **AI模型配置** (至少一个):
   | Secret | 说明 |
   |--------|------|
   | `AIHUBMIX_KEY` | AIHubMix API Key (推荐，一键切换多模型) |
   | `GEMINI_API_KEY` | Google AI Studio (需科学上网) |
   | `ANTHROPIC_API_KEY` | Claude API Key |
   | `OPENAI_API_KEY` | OpenAI兼容Key |
   | `OLLAMA_API_BASE` | 本地Ollama地址 |

   **通知渠道** (至少一个):
   | Secret | 说明 |
   |--------|------|
   | `WECHAT_WEBHOOK_URL` | 企业微信 |
   | `FEISHU_WEBHOOK_URL` | 飞书 |
   | `TELEGRAM_BOT_TOKEN` | Telegram |
   | `DISCORD_WEBHOOK_URL` | Discord |
   | `EMAIL_SENDER` | 发件邮箱 |

3. **配置自选股**:
   - 编辑 `main.py` 或环境变量设置股票列表

4. **运行分析**:
   ```bash
   python main.py
   ```

**本地部署**:
```bash
git clone https://github.com/ZhuLinsen/daily_stock_analysis.git
cd daily_stock_analysis
pip install -r requirements.txt

# 配置环境变量
cp .env.example .env
# 编辑 .env 配置API Key和通知渠道

# 运行分析
python main.py
```

**Docker部署**:
```bash
docker build -t stock-analysis .
docker run -e AIHUBMIX_KEY=xxx -e WECHAT_WEBHOOK_URL=xxx stock-analysis
```

**Web工作台**:
```bash
python webui.py
# 访问 http://localhost:7860
```

## 外部接口

**环境变量配置**:
| 变量 | 说明 | 示例 |
|------|------|------|
| `LITELLM_MODEL` | 主模型 | `gemini-3.1-pro-preview` |
| `LITELLM_FALLBACK_MODELS` | 备选模型 | `claude-3-5-sonnet,gpt-5.2` |
| `LLM_CHANNELS` | 多模型渠道 | `gemini,anthropic,openai` |
| `REPORT_TYPE` | 报告类型 | `simple/full/brief` |
| `REPORT_LANGUAGE` | 报告语言 | `zh/en` |
| `ANALYSIS_DELAY` | 分析延迟(秒) | `10` |
| `MAX_WORKERS` | 并发数 | `3` |

**Web API**:
- `/` - 首页/自选股管理
- `/ask` - 问股/策略对话
- `/backtest` - 回测验证
- `/portfolio` - 持仓管理

**数据源优先级**:
- **A股**: Efinance → AkShare → Tushare → Pytdx → Baostock
- **美股/港股**: Longbridge → YFinance/AkShare
- **美股指数**: YFinance优先

## 数据流 / 控制流

```
GitHub Actions定时触发 / 手动执行
    ↓
拉取多源行情数据 (AkShare/Tushare/Longbridge...)
    ↓
LLM多维度分析 (技术面+基本面+舆情)
    ↓
生成决策仪表盘 (结论+点位+检查清单)
    ↓
多渠道推送 (微信/飞书/Discord...)
    ↓
保存历史记录用于回测验证
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 | 高 |
| LiteLLM | 多LLM统一调用 | 高 |
| AkShare/Tushare | A股数据源 | 高 |
| Longbridge | 美/港股数据源 | 高 |
| YFinance | 美股数据 | 高 |
| Jinja2 | 报告模板 | 高 |
| Gradio | Web界面 | 高 |
| GitHub Actions | 定时执行 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，多语言 | 高 |
| 上手难度 | 低 | GitHub Actions一键部署 | 低 |
| 架构复杂度 | 中 | 多数据源+多LLM+多渠道 | 中 |
| 外部依赖 | 高 | 依赖多个API和数据源 | 高 |
| Stars | 高 | 27.8k stars | 高 |
| 维护状态 | 高 | 活跃开发，504 commits | 高 |

**风险提示**:
- ⚠️ **投资有风险，分析仅供参考，不构成投资建议**
- ⚠️ API调用可能产生费用
- ⚠️ 数据源可能有延迟或不稳定
- ⚠️ 历史回测不代表未来表现

**免责声明**:
> 本项目仅供学习研究，不构成任何投资建议。使用本项目进行的投资决策，风险由用户自行承担。

## 关联概念

- [[A-Share]] - A股市场
- [[Hong-Kong-Stock]] - 港股市场
- [[US-Stock]] - 美股市场
- [[Technical-Analysis]] - 技术分析
- [[Fundamental-Analysis]] - 基本面分析
- [[Gemini]] - Google Gemini模型
- [[Claude]] - Anthropic Claude模型
- [[DeepSeek]] - DeepSeek模型
- [[LiteLLM]] - 多LLM统一调用框架
- [[GitHub-Actions]] - CI/CD自动化
- [[Quantitative-Trading]] - 量化交易
- [[Stock-Analysis]] - 股票分析

---

> 来源: [GitHub](https://github.com/ZhuLinsen/daily_stock_analysis) | 置信度: 基于 GitHub README
> 👤 **作者**: ZhuLinsen
> ⭐ **Stars**: 27.8k
> 🔗 **官网**: [GitHub](https://github.com/ZhuLinsen/daily_stock_analysis)
> 📜 **许可证**: MIT
> ⚠️ **免责声明**: 仅供学习研究，不构成投资建议
