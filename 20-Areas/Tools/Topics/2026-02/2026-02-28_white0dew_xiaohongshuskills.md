---
title: "white0dew/XiaohongshuSkills: 小红书自动化发布Skill (2.4k stars)"
github: "https://github.com/white0dew/XiaohongshuSkills"
owner: white0dew
repo: XiaohongshuSkills
date: 2026-02-28
batch_date: 2026-02-28
type: github-project
tags: [github, python, xiaohongshu, automation, skill, social-media]
pinboard_tags: [ai, automation, xiaohongshu]
source_used: github-readme-extract
source_url: "https://github.com/white0dew/XiaohongshuSkills"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# white0dew/XiaohongshuSkills: 小红书自动化发布Skill

## 一句话概述

小红书自动发布、自动评论、自动检索的Skill命令行工具，通过Chrome DevTools Protocol (CDP)实现自动化，支持多账号管理、无头模式运行、内容数据抓取等功能，支持OpenClaw、Codex、CC等AI工具。

## 项目定位

**目标用户**:
- 需要批量管理小红书内容的创作者
- 希望自动化社交媒体运营的团队
- 需要数据抓取的营销分析师
- 寻求AI辅助内容发布的开发者

**解决的问题**:
- **手动发布效率低**: 逐条发布耗时费力
- **多账号管理困难**: 切换账号流程繁琐
- **内容数据难获取**: 手动抓取费时且易被封
- **评论互动滞后**: 无法及时响应评论

**使用场景**:
- 批量内容发布和定时发布
- 多账号矩阵运营
- 竞品内容监控和分析
- 自动评论和互动
- 首页推荐流数据抓取

**与同类项目差异**:
- **CDP驱动**: 基于Chrome DevTools Protocol，非模拟点击更稳定
- **创作者中心兼容**: 适配2026年2-3月小红书DOM变动
- **话题标签自动**: 识别正文#标签自动写入
- **远程CDP支持**: 可连接远程Chrome调试端口
- **Skill集成**: 可作为Claude Code、OpenCode等Skill使用

## README 中文简介

**RedBookSkills** — 自动发布内容到小红书的命令行工具

通过 Chrome DevTools Protocol (CDP) 实现自动化发布，支持多账号管理、无头模式运行、自动搜索素材与内容数据抓取等功能。

**核心特性**:
- **自动化发布**: 自动填写标题、正文、上传图片
- **创作者中心兼容**: 适配2026年2-3月发布页DOM变动
- **话题标签自动**: 识别正文最后一行#标签，自动写入
- **多账号支持**: Cookie隔离，独立管理多个账号
- **无头模式**: 后台运行，无需显示浏览器窗口
- **远程CDP**: 支持连接远程Chrome调试端口
- **图片下载**: 支持从URL自动下载图片，绕过防盗链
- **登录状态缓存**: 默认本地缓存12小时，减少重复校验

**功能列表**:
- 首页推荐流抓取
- 内容检索与详情读取（含评论数据）
- 笔记评论和回复
- 点赞/取消点赞、收藏/取消收藏
- 用户页信息提取
- 通知评论抓取
- 内容数据看板导出CSV

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| CDP自动化 | Chrome DevTools Protocol驱动 | README | 高 |
| 内容发布 | 自动填写标题、正文、上传图片 | README | 高 |
| 多账号管理 | Cookie隔离，独立配置 | README | 高 |
| 无头模式 | 后台运行，无需窗口 | README | 高 |
| 远程CDP | 支持远程Chrome调试端口 | README | 高 |
| 数据抓取 | 首页feed、详情、评论 | README | 高 |
| 互动操作 | 点赞、收藏、评论、回复 | README | 高 |
| 数据导出 | 内容数据看板导出CSV | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              XiaohongshuSkills 架构                        │
│           (小红书自动化发布Skill)                            │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              Skill接口层 (SKILL.md)                │  │
│  │                                                  │  │
│  │   • Claude Code集成                              │  │
│  │   • OpenCode集成                                 │  │
│  │   • 命令行接口                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              发布流水线层                          │  │
│  │                                                  │  │
│  │   • publish_pipeline.py (统一发布入口)           │  │
│  │   • 标题/正文/图片处理                           │  │
│  │   • 话题标签提取                                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              CDP控制层                             │  │
│  │                                                  │  │
│  │   • cdp_publish.py (底层CDP控制)                 │  │
│  │   • Chrome DevTools Protocol                     │  │
│  │   • 选择器管理                                   │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              浏览器管理层                          │  │
│  │                                                  │  │
│  │   • chrome_launcher.py (Chrome管理)              │  │
│  │   • 有头/无头模式                                │  │
│  │   • 远程CDP连接                                  │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 文件 | 职责 | 关系 |
|------|------|------|------|
| 发布流水线 | `scripts/publish_pipeline.py` | 统一发布入口 | 核心 |
| CDP控制 | `scripts/cdp_publish.py` | 底层CDP操作 | 核心 |
| Chrome管理 | `scripts/chrome_launcher.py` | 浏览器生命周期 | 核心 |
| Skill定义 | `SKILL.md` | AI工具集成配置 | 扩展 |
| 配置管理 | `config/` | 账号和选择器配置 | 核心 |

## 运行与开发方式

**环境要求**:
- Python 3.10+
- Google Chrome浏览器
- Windows操作系统（当前仅测试Windows）

**安装**:
```bash
git clone https://github.com/white0dew/XiaohongshuSkills.git
cd XiaohongshuSkills
pip install -r requirements.txt
```

**首次登录**:
```bash
python scripts/cdp_publish.py login
# 扫码登录小红书
```

**发布内容**:
```bash
# 无头模式发布
python scripts/publish_pipeline.py --headless \
  --title "文章标题" \
  --content "文章正文" \
  --image-urls "https://example.com/image.jpg"

# 有窗口预览模式
python scripts/publish_pipeline.py --preview \
  --title "文章标题" \
  --content "文章正文" \
  --image-urls "URL"

# 从文件读取内容
python scripts/publish_pipeline.py --headless \
  --title-file title.txt \
  --content-file content.txt \
  --image-urls "URL"
```

**多账号管理**:
```bash
# 列出所有账号
python scripts/cdp_publish.py list-accounts

# 添加新账号
python scripts/cdp_publish.py add-account myaccount --alias "我的账号"

# 使用指定账号发布
python scripts/publish_pipeline.py --account myaccount --headless \
  --title "标题" --content "正文" --image-urls "URL"
```

**内容抓取**:
```bash
# 首页推荐列表
python scripts/cdp_publish.py list-feeds

# 搜索笔记
python scripts/cdp_publish.py search-feeds --keyword "春招"

# 获取笔记详情
python scripts/cdp_publish.py get-feed-detail \
  --feed-id 67abc1234def567890123456 \
  --xsec-token YOUR_XSEC_TOKEN

# 导出内容数据CSV
python scripts/cdp_publish.py content-data --csv-file "/path/content_data.csv"
```

**评论互动**:
```bash
# 发表评论
python scripts/cdp_publish.py post-comment-to-feed \
  --feed-id FEED_ID --xsec-token XSEC_TOKEN \
  --content "写得很实用，感谢分享！"

# 回复评论
python scripts/cdp_publish.py respond-comment \
  --feed-id FEED_ID --xsec-token XSEC_TOKEN \
  --comment-id COMMENT_ID --content "感谢反馈～"

# 点赞/收藏
python scripts/cdp_publish.py note-upvote --feed-id FEED_ID --xsec-token TOKEN
python scripts/cdp_publish.py note-bookmark --feed-id FEED_ID --xsec-token TOKEN
```

## 外部接口

**publish_pipeline.py 参数**:
| 参数 | 说明 |
|------|------|
| `--title` | 文章标题 |
| `--content` | 文章正文 |
| `--image-urls` | 图片URL列表 |
| `--images` | 本地图片文件列表 |
| `--headless` | 无头模式 |
| `--preview` | 预览模式（仅填充不发布）|
| `--account` | 指定账号 |
| `--host`/`--port` | 远程CDP地址 |
| `--reuse-existing-tab` | 复用已有标签页 |

**话题标签规则**:
- 正文最后一行全部由`#标签`组成时自动提取
- 逐个输入`#标签`，等待3秒，再发送Enter确认
- 建议数量：1-10个标签

**注意事项**:
- 仅供学习研究，请遵守小红书平台规则
- Cookie存储在本地Chrome Profile中，请勿泄露
- 如页面结构变化需更新`cdp_publish.py`中的选择器

## 数据流 / 控制流

```
用户命令/Skill调用
    ↓
publish_pipeline.py 解析参数
    ↓
cdp_publish.py CDP操作
    ↓
Chrome DevTools Protocol
    ↓
小红书创作者中心页面
    ↓
内容发布/数据抓取/互动操作
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Python | 主要语言 (100%) | 高 |
| Chrome DevTools Protocol | 浏览器自动化 | 高 |
| CDP (Chrome DevTools Protocol) | 核心通信协议 | 高 |
| OpenClaw/Codex/CC Skill | AI工具集成 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详细README，含大量示例 | 高 |
| 上手难度 | 中 | 需要Python环境和Chrome | 中 |
| 架构复杂度 | 中 | CDP + 多账号 + 数据抓取 | 中 |
| 外部依赖 | 高 | 依赖小红书页面结构 | 高 |
| Stars | 中 | 2.4k stars | 中 |
| 维护状态 | 高 | 活跃更新（适配2026年2-3月改版） | 高 |

**风险提示**:
- ⚠️ 仅供学习研究，遵守平台规则
- ⚠️ 页面结构变化可能导致失效
- ⚠️ 频繁操作可能触发风控

## 关联概念

- [[Chrome-DevTools-Protocol]] - Chrome开发者工具协议
- [[Xiaohongshu]] - 小红书平台
- [[OpenClaw]] - AI Agent框架
- [[Claude-Code]] - Anthropic Claude Code
- [[Social-Media-Automation]] - 社交媒体自动化
- [[CDP]] - Chrome DevTools Protocol
- [[RedBook]] - 小红书(RED)

---

> 来源: [GitHub](https://github.com/white0dew/XiaohongshuSkills) | 置信度: 基于 GitHub README
> 👤 **作者**: white0dew
> ⭐ **Stars**: 2.4k
> 🔗 **官网**: [GitHub](https://github.com/white0dew/XiaohongshuSkills)
> 📜 **许可证**: MIT
