---
title: "laravel/framework: PHP Web 应用框架 (34.6k stars)"
github: "https://github.com/laravel/framework"
owner: laravel
repo: framework
date: 2026-02-05
batch_date: 2026-02-05
type: github-project
tags: [github, php, web-framework, laravel, mvc, backend]
pinboard_tags: [php, web-framework, backend]
source_used: github-readme-extract
source_url: "https://github.com/laravel/framework"
source_quality: repo_text_extract
readme_backed: true
needs_verification: false
---

# laravel/framework: PHP Web 应用框架

## 一句话概述

Laravel 是一个表达力强、语法优雅的 PHP Web 应用框架，提供简洁快速的路由、强大的依赖注入、多后端会话/缓存、数据库无关的迁移、稳健的后台作业和实时事件广播，让开发成为愉快创造性的体验。

## 项目定位

**目标用户**:
- PHP Web 开发者
- 需要快速构建 Web 应用的团队
- 追求代码优雅和开发效率的工程师
- 全栈开发者和创业公司

**解决的问题**:
- **PHP 开发繁琐**: 传统 PHP 开发缺乏现代框架支持
- **代码组织混乱**: 没有统一的项目结构和最佳实践
- **重复造轮子**: 每个项目重复实现认证、路由、ORM 等功能
- **部署复杂**: 缺乏现代部署和 CI/CD 支持
- **扩展困难**: 应用难以维护和扩展

**使用场景**:
- 企业级 Web 应用开发
- RESTful API 构建
- 电商平台
- 内容管理系统
- 实时应用(配合 Laravel Echo)

**与同类项目差异**:
- **优雅语法**: 表达力强、直观的 API 设计
- **完整生态**: 官方提供 Forge、Vapor、Nova、Echo 等配套产品
- **现代 PHP**: 充分利用 PHP 最新特性
- **活跃社区**: 丰富的扩展包和详尽的文档
- **商业支持**: Laravel LLC 提供商业产品和服务

## README 中文简介

**Laravel Framework** - PHP Web 应用框架核心代码

注意: 此仓库包含 Laravel 框架的核心代码。如果要使用 Laravel 构建应用，请访问 [主 Laravel 仓库](https://github.com/laravel/laravel)。

**关于 Laravel**:

Laravel 是一个具有表达力强、语法优雅的 Web 应用框架。我们相信开发必须是一种愉快、创造性的体验才能真正充实。Laravel 试图通过简化 Web 项目中常见的任务来消除开发的痛苦:

- **简单快速的路由引擎**
- **强大的依赖注入容器**
- **多后端会话和缓存存储**
- **数据库无关的架构迁移**
- **稳健的后台作业处理**
- **实时事件广播**

Laravel 易于上手但功能强大，提供了构建任何规模应用所需的工具。简洁、优雅和创新的完美结合为您提供了构建任何任务应用所需的完整工具集。

**学习 Laravel**:

Laravel 拥有所有现代 Web 应用框架中最广泛和详尽的视频教程库，让您可以轻松入门。您还可以查看 [Laravel Learn](https://learn.laravel.com)，在其中您将被引导构建一个现代 Laravel 应用。

如果您不想阅读，[Laracasts](https://laracasts.com) 包含数千个视频教程，涵盖 Laravel、现代 PHP、单元测试、JavaScript 等主题。通过深入研究我们的综合视频库，提升自己和整个团队的技能水平。

您还可以在 [Laravel Learn](https://learn.laravel.com) 上观看带有真实项目的 bite-sized 课程，在学习 PHP 基础知识的同时，您将被引导从头开始构建一个 Laravel 应用。

**贡献**:

感谢您对 Laravel 框架的贡献！贡献指南可在 Laravel 文档中找到。

**行为准则**:

为确保 Laravel 社区欢迎所有人，请查看并遵守我们的行为准则。

**安全漏洞**:

请查看我们的安全政策，了解如何报告安全漏洞。

**许可证**:

Laravel 框架是遵循 MIT 许可证的开源软件。

## 核心能力

| 能力 | 说明 | 证据来源 | 置信度 |
|------|------|----------|--------|
| 路由引擎 | 简单快速的路由定义 | README | 高 |
| 依赖注入 | 强大的 IoC 容器 | README | 高 |
| 会话/缓存 | 多后端存储支持 | README | 高 |
| 数据库迁移 | 数据库无关的架构版本控制 | README | 高 |
| 后台作业 | 稳健的作业队列处理 | README | 高 |
| 事件广播 | 实时事件系统 | README | 高 |
| Eloquent ORM | 优雅的数据库模型 | README | 高 |
| Blade 模板 | 轻量级模板引擎 | README | 高 |
| Artisan CLI | 命令行工具 | README | 高 |
| 测试支持 | PHPUnit 集成 | README | 高 |

## 技术架构

```
┌─────────────────────────────────────────────────────────┐
│              Laravel 架构                                  │
│           (PHP Web 应用框架)                                │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌─────────────────────────────────────────────────┐  │
│  │              应用层                                │  │
│  │                                                  │  │
│  │   • 路由 (Routes)                                │  │
│  │   • 控制器 (Controllers)                         │  │
│  │   • 中间件 (Middleware)                          │  │
│  │   • 请求/响应 (Request/Response)                 │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              服务层                                │  │
│  │                                                  │  │
│  │   ┌──────────────┬──────────────┬──────────────┐│  │
│  │   │ Eloquent     │ Blade        │ Artisan      ││  │
│  │   │ ORM          │ Templates    │ CLI          ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ Queue        │ Events       │ Broadcasting ││  │
│  │   │ (作业队列)   │ (事件系统)   │ (实时广播)   ││  │
│  │   ├──────────────┼──────────────┼──────────────┤│  │
│  │   │ Cache        │ Session      │ Mail         ││  │
│  │   │ (缓存)       │ (会话)       │ (邮件)       ││  │
│  │   └──────────────┴──────────────┴──────────────┘│  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                          │                               │
│                          ▼                               │
│  ┌─────────────────────────────────────────────────┐  │
│  │              基础设施层                            │  │
│  │                                                  │  │
│  │   • 依赖注入容器 (Container)                     │  │
│  │   • 服务提供者 (Service Providers)               │  │
│  │   • 外观/门面 (Facades)                          │  │
│  │   • 配置系统 (Config)                            │  │
│  │                                                  │  │
│  └─────────────────────────────────────────────────┘  │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## 关键模块映射

| 模块 | 目录 | 职责 | 关系 |
|------|------|------|------|
| 核心框架 | `src/Illuminate/` | 框架核心组件 | 核心 |
| 数据库 | `src/Illuminate/Database/` | Eloquent ORM、迁移 | 核心 |
| 路由 | `src/Illuminate/Routing/` | 路由系统 | 核心 |
| 视图 | `src/Illuminate/View/` | Blade 模板 | 核心 |
| 缓存 | `src/Illuminate/Cache/` | 缓存系统 | 核心 |
| 队列 | `src/Illuminate/Queue/` | 作业队列 | 核心 |
| 容器 | `src/Illuminate/Container/` | 依赖注入 | 核心 |

## 运行与开发方式

**快速开始**:

**创建新项目**:
```bash
composer create-project laravel/laravel my-app
cd my-app
php artisan serve
```

**核心框架开发**:
```bash
# 克隆框架仓库
git clone https://github.com/laravel/framework.git
cd framework

# 安装依赖
composer install

# 运行测试
vendor/bin/phpunit
```

**常用命令**:
```bash
# 创建控制器
php artisan make:controller UserController

# 创建模型+迁移
php artisan make:model User -m

# 运行迁移
php artisan migrate

# 创建作业
php artisan make:job ProcessPodcast

# 启动队列
php artisan queue:work
```

**使用框架核心**:
```php
<?php

use Illuminate\Container\Container;
use Illuminate\Events\Dispatcher;
use Illuminate\Database\Capsule\Manager as Capsule;

// 创建容器
$container = new Container;
$dispatcher = new Dispatcher($container);

// 数据库管理器
$capsule = new Capsule;
$capsule->addConnection([
    'driver' => 'mysql',
    'host' => 'localhost',
    'database' => 'mydb',
    'username' => 'root',
    'password' => '',
    'charset' => 'utf8',
    'collation' => 'utf8_unicode_ci',
    'prefix' => '',
]);
$capsule->setAsGlobal();
$capsule->bootEloquent();
```

## 外部接口

**Artisan 命令**:
| 命令 | 功能 |
|------|------|
| `make:model` | 创建 Eloquent 模型 |
| `make:controller` | 创建控制器 |
| `make:migration` | 创建数据库迁移 |
| `migrate` | 执行迁移 |
| `make:middleware` | 创建中间件 |
| `make:command` | 创建 Artisan 命令 |
| `make:job` | 创建队列作业 |
| `queue:work` | 处理队列作业 |
| `cache:clear` | 清除缓存 |
| `route:list` | 列出所有路由 |

**核心组件**:
| 组件 | 功能 |
|------|------|
| Container | 依赖注入容器 |
| Router | 路由管理 |
| Eloquent | ORM 数据库操作 |
| Blade | 模板引擎 |
| Cache | 缓存管理 |
| Session | 会话管理 |
| Queue | 队列作业 |
| Mail | 邮件发送 |
| Auth | 认证系统 |
| Event | 事件系统 |

## 数据流 / 控制流

```
HTTP 请求
    ↓
入口文件 (public/index.php)
    ↓
创建应用实例 (bootstrap/app.php)
    ↓
内核处理 (Http Kernel)
    ↓
中间件管道
    ↓
路由匹配
    ↓
控制器/闭包执行
    ↓
    ├─ Eloquent ORM 数据库操作
    ├─ Cache/Session 读写
    └─ Queue 作业分发
    ↓
响应生成 (View/JSON)
    ↓
中间件后置处理
    ↓
返回 HTTP 响应
```

## 技术栈判断

| 技术 | 依据 | 置信度 |
|------|------|--------|
| PHP | 主要语言 (99.4%) | 高 |
| Composer | 包管理 | 高 |
| PHPUnit | 测试框架 | 高 |
| MySQL/PostgreSQL/SQLite | 数据库支持 | 高 |
| Redis | 缓存/队列后端 | 高 |
| Docker | 开发环境 | 中 |

## 成熟度与风险

| 维度 | 评估 | 说明 |
|------|------|------|
| 文档完整度 | 高 | 详尽文档、视频教程、社区丰富 | 高 |
| 上手难度 | 中 | 需要 PHP 基础，框架概念学习曲线 | 中 |
| 架构复杂度 | 中 | 现代 PHP 框架架构 | 中 |
| 外部依赖 | 低 | Composer 生态丰富 | 低 |
| Stars | 高 | 34.6k stars (框架核心) | 高 |
| 维护状态 | 高 | 持续更新，v13.x 活跃开发 | 高 |

**生态产品**:
- **Laravel Forge**: 服务器管理
- **Laravel Vapor**: 无服务器部署
- **Laravel Nova**: 管理面板
- **Laravel Echo**: 实时事件
- **Laravel Dusk**: 浏览器测试
- **Laravel Sanctum**: API 认证
- **Laravel Scout**: 全文搜索
- **Laravel Horizon**: 队列监控

**注意事项**:
- 框架核心仓库仅包含核心组件
- 应用开发使用 laravel/laravel 骨架
- 关注性能优化(缓存、队列)
- 保持框架和依赖更新

## 关联概念

- [[PHP]] - PHP 编程语言
- [[MVC]] - Model-View-Controller 架构
- [[ORM]] - 对象关系映射
- [[Dependency-Injection]] - 依赖注入
- [[Composer]] - PHP 包管理器
- [[Eloquent]] - Laravel ORM
- [[Blade]] - Laravel 模板引擎
- [[Artisan]] - Laravel CLI

---

> 来源: [GitHub](https://github.com/laravel/framework) | 置信度: 基于 GitHub README
> 👤 **作者**: Taylor Otwell (Laravel LLC)
> ⭐ **Stars**: 34.6k (框架核心)
> 🔗 **官网**: [laravel.com](https://laravel.com)
> 💰 **公司**: Laravel LLC
> 📜 **许可证**: MIT
