---
title: "greekr4/playwright-bot-bypass: Playwright 反检测 Skill (138 stars)"
github: "https://github.com/greekr4/playwright-bot-bypass"
owner: greekr4
repo: playwright-bot-bypass
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, playwright, bot-detection, scraping, stealth]
pinboard_tags: [playwright, scraping, stealth]
source_used: github-readme-extract
source_url: "https://github.com/greekr4/playwright-bot-bypass"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# greekr4/playwright-bot-bypass: Playwright 反检测 Skill

## 一句话概述

playwright-bot-bypass 是一个 Claude Code Skill，使用 rebrowser-playwright (Node.js) 或 undetected-chromedriver (Python) 绕过机器人检测，支持 Twitter/X 无登录抓取、Google 搜索无验证码。

## 项目定位

**目标用户**:
- 需要绕过机器人检测的 Web 抓取开发者
- 使用 Claude Code 进行网页自动化的用户
- 寻求 Camofox/Nitter 替代方案的技术人员
- 需要无头浏览器隐身功能的工程师

**解决的问题**:
- **机器人检测**: 标准 Playwright 容易被网站检测为机器人
- **Camofox 被阻**: Camofox 和 Nitter 等工具被 Twitter/X 封锁
- **验证码困扰**: Google 搜索频繁触发验证码
- **WebDriver 暴露**: 标准的 navigator.webdriver = true 暴露自动化痕迹
- **GPU 指纹**: 需要真实的 GPU 指纹模拟

**使用场景**:
- Twitter/X 数据抓取无需登录
- Google 搜索自动化
- 绕过 bot.sannysoft.com 检测
- 需要隐身模式的网页抓取

**与同类项目差异**:
- **Skill 形式**: 作为 Claude Code Skill 提供，易于集成
- **双语言支持**: 同时支持 Node.js (rebrowser-playwright) 和 Python (undetected-chromedriver)
- **真实 GPU 指纹**: 模拟 Apple M2、NVIDIA 等真实 GPU
- **WebDriver 移除**: 完全移除 navigator.webdriver 属性

## README 中文简介

**playwright-bot-bypass** - 绕过机器人检测的 Claude Code Skill

**🔥 Camofox + Nitter 被阻？这可以作为 Twitter/X 无登录抓取的替代方案。**

使用 rebrowser-playwright (Node.js) 或 undetected-chromedriver (Python) 绕过机器人检测的 Claude Code Skill。

**安装**:
```bash
npx skills add greekr4/playwright-bot-bypass
```

**功能**:

| 功能 | 说明 |
|------|------|
| ✅ bot.sannysoft.com | 通过所有测试 |
| ✅ Google 搜索 | 无需验证码 |
| ✅ Twitter/X 抓取 | 无需登录 |
| ✅ 真实 GPU 指纹 | Apple M2、NVIDIA 等 |
| ✅ WebDriver 移除 | 完全移除 navigator.webdriver |
| ✅ 多语言支持 | Node.js 和 Python |

**A/B 测试: 标准 vs 隐身**

**标准 Playwright (被检测)**:
- 暴露 navigator.webdriver = true（红色警告）

**rebrowser-playwright (绕过)**:
- 完全移除 navigator.webdriver（绿色通过）

左图：标准 Playwright 暴露 navigator.webdriver = true（红色）
右图：rebrowser-playwright 完全移除它（绿色）

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 反检测 | 绕过 bot.sannysoft.com 检测 | README | 高 |
| Google 搜索 | 无需验证码搜索 | README | 高 |
| Twitter/X 抓取 | 无登录抓取推文 | README | 高 |
| GPU 指纹 | 真实 GPU 指纹模拟 | README | 高 |
| WebDriver 隐藏 | 移除 webdriver 属性 | README | 高 |
| Node.js 支持 | rebrowser-playwright | README | 高 |
| Python 支持 | undetected-chromedriver | README | 高 |
| Skill 安装 | npx skills add | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              playwright-bot-bypass 架构                    │
│           (反检测浏览器自动化)                               │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Skill 层 (Claude Code)                │  │
│  │                                                  │  │
│  │   • Skill 定义                                    │  │
│  │   • 命令封装                                     │  │
│  │   • 配置管理                                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              浏览器层                              │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┐              │  │
│  │   │ rebrowser-   │ undetected-  │              │  │
│  │   │ playwright   │ chromedriver │              │  │
│  │   │ (Node.js)    │ (Python)     │              │  │
│  │   ├──────────────┼──────────────┤              │  │
│  │   │ 真实 GPU     │ WebDriver    │              │  │
│  │   │ 指纹         │ 隐藏         │              │  │
│  │   └──────────────┴──────────────┘              │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              目标网站层                            │  │
│  │                                                  │  │
│  │   • bot.sannysoft.com (检测测试)                │  │
│  │   • Google 搜索                                  │  │
│  │   • Twitter/X                                    │  │
│  │   • 其他需要隐身访问的网站                       │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| Skill | `skills/playwright-bot-bypass/` | Claude Code Skill | 核心 |
| Node.js | `skills/playwright-bot-bypass/` | rebrowser-playwright 实现 | 核心 |
| Python | (通过 undetected-chromedriver) | Python 实现 | 核心 |

## 运行与开发方式

**安装 Skill**:
```bash
npx skills add greekr4/playwright-bot-bypass
```

**使用**:
```bash
# 在 Claude Code 中使用
/playwright-bot-bypass --url "https://twitter.com/search?q=claude"
```

**Node.js 方式**:
```javascript
const { chromium } = require('rebrowser-playwright');

(async () => {
  const browser = await chromium.launch();
  const page = await browser.newPage();
  await page.goto('https://twitter.com');
  // ... 抓取逻辑
})();
```

**Python 方式**:
```python
import undetected_chromedriver as uc

driver = uc.Chrome()
driver.get('https://twitter.com')
# ... 抓取逻辑
```

**开发**:
```bash
# 克隆仓库
git clone https://github.com/greekr4/playwright-bot-bypass.git
```

## 外部接口

**Skill 命令**:
| 命令 | 功能 |
|------|------|
| `playwright-bot-bypass` | 运行反检测浏览器 |
| `--url <url>` | 指定目标 URL |
| `--headless` | 无头模式 |

**rebrowser-playwright API**:
兼容标准 Playwright API，但添加了反检测特性

**undetected-chromedriver API**:
兼容标准 Selenium API，但自动绕过检测

## 数据流 / 控制流

```
Claude Code Skill 调用
    ↓
选择实现 (Node.js/Python)
    ↓
启动反检测浏览器
    ↓
(绕过检测机制)
    ↓
访问目标网站
    ↓
执行抓取/自动化任务
    ↓
返回结果
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Node.js | rebrowser-playwright | 高 |
| Python | undetected-chromedriver | 高 |
| Playwright | 浏览器自动化 | 高 |
| Selenium | 备选方案 | 中 |
| Chromium | 浏览器内核 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README 清晰，有 A/B 测试对比 | 中 |
| 上手难度 | 低 | Skill 形式，一行命令安装 | 低 |
| 架构复杂度 | 低 | 封装现有工具 | 低 |
| 外部依赖 | 中 | 依赖 rebrowser-playwright/undetected-chromedriver | 中 |
| Stars | 低 | 138 stars | 低 |
| 维护状态 | 中 | 较新项目 | 中 |

**注意事项**:
- 反检测技术可能随时被网站更新检测
- 使用时需遵守网站服务条款
- Twitter/X 可能随时更新反爬机制

**替代方案对比**:
| 工具 | 状态 | 说明 |
|------|------|------|
| Camofox | 被阻 | 被 Twitter/X 封锁 |
| Nitter | 被阻 | 被 Twitter/X 封锁 |
| playwright-bot-bypass | 可用 | 当前可行方案 |

## 关联概念

- [[Playwright]] - 浏览器自动化工具
- [[Selenium]] - 浏览器自动化工具
- [[Web-Scraping]] - 网页抓取
- [[Bot-Detection]] - 机器人检测
- [[Stealth-Browser]] - 隐身浏览器
- [[rebrowser-playwright]] - 反检测 Playwright
- [[undetected-chromedriver]] - 反检测 Selenium

---

> 来源: [GitHub](https://github.com/greekr4/playwright-bot-bypass) | 置信度: 基于 GitHub README
> 👤 **作者**: greekr4
> ⭐ **Stars**: 138
> 🔗 **官网**: [GitHub](https://github.com/greekr4/playwright-bot-bypass)
> 📜 **许可证**: MIT
