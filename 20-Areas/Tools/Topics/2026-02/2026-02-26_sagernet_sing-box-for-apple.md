---
title: "SagerNet/sing-box-for-apple: sing-box iOS/macOS客户端 (806 stars)"
github: "https://github.com/SagerNet/sing-box-for-apple"
owner: SagerNet
repo: sing-box-for-apple
date: 2026-02-26
batch_date: 2026-02-26
type: github-project
tags: [github, swift, ios, macos, vpn, proxy, sing-box, network]
pinboard_tags: [mac, vpn]
source_used: github-readme-extract
source_url: "https://github.com/SagerNet/sing-box-for-apple"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# SagerNet/sing-box-for-apple: sing-box iOS/macOS客户端

## 一句话概述

sing-box的实验性iOS/macOS/tvOS客户端，基于Swift开发，是通用代理平台sing-box在Apple生态系统的原生客户端实现。

## 项目定位

**目标用户**:
- 需要在iOS/macOS上使用sing-box的开发者
- 寻求代理工具替代品的Apple用户
- 需要自定义代理规则的高级用户
- 关注网络隐私和安全的用户

**解决的问题**:
- **iOS/macOS代理工具选择少**: 优质开源代理客户端稀缺
- **配置复杂**: 传统代理工具配置门槛高
- **系统集成差**: 第三方代理工具与系统集成度低
- **性能问题**: 现有工具性能或稳定性不足

**使用场景**:
- iPhone/iPad代理上网
- Mac电脑代理配置
- Apple TV代理设置
- 自定义路由规则
- 多协议代理支持

**与同类项目差异**:
- **sing-box生态**: 基于sing-box通用代理平台，协议支持全面
- **原生Apple体验**: Swift开发，原生iOS/macOS/tvOS支持
- **实验性项目**: 探索新特性和架构的前沿实现
- **开源免费**: GPL v3许可，完全开源

## README 中文简介

**sing-box-for-apple**

Experimental iOS/macOS/tvOS client for sing-box, the universal proxy platform.

**项目性质**:
- 实验性项目 (Experimental)
- sing-box官方Apple平台客户端
- 持续开发和迭代中

**支持平台**:
- iOS (iPhone/iPad)
- macOS
- tvOS (Apple TV)

**文档**:
- [SFI Documentation](https://sing-box.sagernet.org/)
- [SFM Documentation](https://sing-box.sagernet.org/)

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| iOS支持 | iPhone/iPad原生客户端 | README | 高 |
| macOS支持 | Mac原生客户端 | README | 高 |
| tvOS支持 | Apple TV客户端 | README | 高 |
| sing-box兼容 | 通用代理平台协议 | README | 高 |
| Swift开发 | 原生Apple技术栈 | GitHub | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              sing-box-for-apple 架构                       │
│           (sing-box Apple平台客户端)                        │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   • SFI (iOS/iPadOS App)                         │  │
│  │   • SFM (macOS App)                              │  │
│  │   • SFT (tvOS App)                               │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              系统扩展层 (System Extension)         │  │
│  │                                                  │  │
│  │   • Network Extension (VPN隧道)                  │  │
│  │   • Intents Extension (快捷指令)                  │  │
│  │   • Widget Extension (小组件)                     │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              sing-box核心层                        │  │
│  │                                                  │  │
│  │   • 代理协议实现 (VMess/VLESS/Trojan等)          │  │
│  │   • 路由引擎                                     │  │
│  │   • DNS解析                                      │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| iOS应用 | `SFI/` | iPhone/iPad主应用 | 核心 |
| macOS应用 | `SFM/` | Mac主应用 | 核心 |
| tvOS应用 | `SFT/` | Apple TV应用 | 核心 |
| 系统扩展 | `Extension/` | Network/Intents扩展 | 核心 |
| 库依赖 | `Library/` | 共享库代码 | 核心 |
| 框架 | `Frameworks/` | 外部框架依赖 | 依赖 |

## 运行与开发方式

**环境要求**:
- macOS (开发需要)
- Xcode (iOS/macOS/tvOS开发)
- Swift 5.0+

**构建步骤**:
```bash
git clone https://github.com/SagerNet/sing-box-for-apple.git
cd sing-box-for-apple

# 初始化子模块
git submodule update --init --recursive

# 打开Xcode项目
open sing-box.xcodeproj

# 在Xcode中构建运行 (Cmd+R)
```

**构建配置**:
- 需要有效的Apple Developer账号
- 配置Provisioning Profile
- 启用Network Extension权限

**依赖管理**:
- Swift Package Manager
- Git子模块 (sing-box核心库)

## 外部接口

**sing-box配置**:
支持sing-box标准JSON配置格式:
```json
{
  "log": {
    "level": "info"
  },
  "inbounds": [
    {
      "type": "mixed",
      "listen": "127.0.0.1",
      "listen_port": 1080
    }
  ],
  "outbounds": [
    {
      "type": "vmess",
      "server": "example.com",
      "server_port": 443,
      "uuid": "..."
    }
  ]
}
```

**支持的协议**:
- VMess / VLESS
- Trojan
- Shadowsocks / ShadowsocksR
- HTTP / SOCKS
- WireGuard
- Hysteria / Hysteria2
- Tuic
- 更多sing-box支持的协议

## 数据流 / 控制流

```
用户操作 (App界面)
    ↓
系统扩展 (Network Extension)
    ↓
sing-box核心引擎
    ↓
代理协议处理 (VMess/VLESS/Trojan...)
    ↓
网络流量转发
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| Swift | 主要语言 (90.1%) | 高 |
| C | 底层实现 (8.3%) | 高 |
| Xcode | 开发环境 | 高 |
| Network Extension | VPN隧道 | 高 |
| sing-box | 代理核心 | 高 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 中 | README简洁，指向外部文档 | 中 |
| 上手难度 | 高 | 需要Xcode和Apple Developer | 高 |
| 架构复杂度 | 中 | 系统扩展+原生应用 | 中 |
| 外部依赖 | 中 | 依赖sing-box核心库 | 中 |
| Stars | 中 | 806 stars | 中 |
| 维护状态 | 中 | 实验性项目，311 commits | 中 |

**风险提示**:
- ⚠️ **实验性项目**: 功能和接口可能变化
- ⚠️ **需要Apple Developer**: 个人开发需要$99年费
- ⚠️ **Network Extension**: 需要特殊权限
- ⚠️ **地区限制**: 某些地区可能无法使用相关功能

**许可证**:
```
Copyright (C) 2022 by nekohasekai
GNU General Public License v3.0
```

## 关联概念

- [[sing-box]] - 通用代理平台
- [[SagerNet]] - sing-box开发团队
- [[Network-Extension]] - iOS/macOS VPN扩展
- [[VMess]] - V2Ray协议
- [[VLESS]] - 轻量级代理协议
- [[Trojan]] - 伪装HTTPS代理
- [[Shadowsocks]] - 轻量级代理协议
- [[WireGuard]] - 现代VPN协议
- [[Swift]] - Apple开发语言
- [[GPL-v3]] - 开源许可证

---

> 来源: [GitHub](https://github.com/SagerNet/sing-box-for-apple) | 置信度: 基于 GitHub README
> 👤 **作者**: SagerNet / nekohasekai
> ⭐ **Stars**: 806
> 🔗 **官网**: [sing-box文档](https://sing-box.sagernet.org/)
> 📜 **许可证**: GNU GPL v3
> ⚠️ **状态**: 实验性项目 (Experimental)
