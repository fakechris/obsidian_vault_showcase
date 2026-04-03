---
title: "Adversarial Review"
type: evergreen
date: 2026-03-31
tags: [evergreen, AI, Agent, review, adversarial, multi-model, quality-assurance]
aliases: [Cross-Model-Review, Adversarial-Validation, Multi-Model-Review]
---

# Adversarial Review

> **一句话定义**: 对抗性审查是通过跨模型（如Claude vs Codex）的对抗性评估来提升代码质量和发现隐蔽缺陷的方法论，核心洞察是"不同模型的失败模式不同，交叉验证能发现单一模型遗漏的问题"——通过Skeptic、Architect、Minimalist三Lens系统性审视输出。

---

## 详细解释

### 为什么需要对抗性审查?

**单一模型审查的局限**:
```
模型A的优势 → 模型A的盲区
• Claude的结构化思维  → 可能遗漏创造性的边界情况
• Codex的代码生成能力 → 可能忽视架构层面的问题
• GPT-4的广泛知识    → 可能缺乏对特定模式的敏感度
```

**跨模型审查的核心洞察**:
> "不同模型有不同的训练数据、优化目标和失败模式。让一个模型审查另一个模型的输出，可以捕捉到单一视角无法发现的问题。"

---

## 三Lens审查框架

### Lens 1: Skeptic (怀疑者)

**视角**: "这能正常工作吗?"

**关注点**:
| 检查项 | 问题 | 示例 |
|--------|------|------|
| 边界条件 | 极端输入会失败吗? | 空数组、超大数字、特殊字符 |
| 并发安全 | 多线程/多进程安全吗? | 竞态条件、死锁风险 |
| 错误处理 | 所有失败路径覆盖了吗? | 网络超时、磁盘满、权限拒绝 |
| 资源泄漏 | 连接/内存会泄漏吗? | 未关闭的文件句柄、数据库连接 |

**典型质疑**:
- "如果API返回500错误会怎样?"
- "这个循环在数据量为0时能退出吗?"
- "资源在异常情况下会被清理吗?"

---

### Lens 2: Architect (架构师)

**视角**: "这符合系统设计吗?"

**关注点**:
| 检查项 | 问题 | 示例 |
|--------|------|------|
| 职责分离 | 每个组件职责清晰吗? | 业务逻辑与数据访问混杂 |
| 依赖关系 | 依赖方向正确吗? | 低层模块依赖高层抽象 |
| 可测试性 | 容易单元测试吗? | 硬编码依赖、全局状态 |
| 扩展性 | 未来需求变化容易修改吗? | 硬编码配置、魔法数字 |

**典型质疑**:
- "这个功能应该属于这个模块吗?"
- "如果需求变更，需要修改多少处代码?"
- "新开发者能理解这个设计吗?"

---

### Lens 3: Minimalist (极简主义者)

**视角**: "这能更简洁吗?"

**关注点**:
| 检查项 | 问题 | 示例 |
|--------|------|------|
| 代码冗余 | 有重复逻辑吗? | 复制粘贴的代码块 |
| 过度设计 | 解耦了不需要解耦的东西吗? | 只有一个实现者的抽象接口 |
| 复杂性 | 有更简单的实现方式吗? | 用递归代替简单的循环 |
| 依赖数量 | 引入的依赖必要吗? | 为一个小功能引入大库 |

**典型质疑**:
- "这行代码真的必要吗?"
- "这个抽象带来了什么价值?"
- "标准库能完成这个功能吗?"

---

## 跨模型对抗流程

### 标准审查流程

```
┌─────────────────────────────────────────────────────────────┐
│                   对抗性审查流程                             │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Step 1: 原始生成                                            │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐                  │
│  │ 模型A   │───►│ 生成    │───►│ 输出O1  │                  │
│  │ (Claude)│    │ 代码/文本│    │         │                  │
│  └─────────┘    └─────────┘    └────┬────┘                  │
│                                     │                        │
│  Step 2: 交叉审查                                            │
│                                     ▼                        │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐                  │
│  │ 模型B   │◄──►│ 三Lens  │◄──►│ 输出O1  │                  │
│  │ (Codex) │    │ 审查    │    │ (输入)  │                  │
│  │         │    ├─Skeptic │    │         │                  │
│  │         │    ├─Architect│   │         │                  │
│  │         │    ├─Minimalist│  │         │                  │
│  └────┬────┘    └─────────┘    └─────────┘                  │
│       │                                                      │
│       ▼                                                      │
│  Step 3: 生成审查报告                                        │
│  ┌─────────────────────────────────────────┐                │
│  │ 审查报告                                 │                │
│  │ ├── 严重问题 (阻塞性问题)                │                │
│  │ ├── 改进建议 (非阻塞性优化)               │                │
│  │ ├── 疑问澄清 (需要确认的点)               │                │
│  │ └── 正面确认 (做得好的地方)               │                │
│  └─────────────────────────────────────────┘                │
│       │                                                      │
│       ▼                                                      │
│  Step 4: 迭代修复                                            │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐                  │
│  │ 模型A   │◄──►│ 修复    │◄──►│ 审查报告│                  │
│  │ (或人)  │    │ 问题    │    │         │                  │
│  └────┬────┘    └─────────┘    └─────────┘                  │
│       │                                                      │
│       ▼                                                      │
│  Step 5: 验证闭环                                            │
│  ┌─────────┐    ┌─────────┐                                 │
│  │ 模型B   │───►│ 验证修复 │───► [通过/未通过]              │
│  │ (再次)  │    │         │                                 │
│  └─────────┘    └─────────┘                                 │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## Brain Principles 集成

对抗性审查与Brain Principles的关联:

| Brain Principle | 在审查中的体现 |
|-----------------|---------------|
| ** layered thinking** | Skeptic → Architect → Minimalist 三层递进 |
| **conflict as signal** | 模型分歧指示需要关注的区域 |
| **compression target** | Minimalist Lens强制压缩冗余 |
| **explicit over implicit** | 所有质疑都必须具体化、可验证 |
| **reversibility** | 审查发现的问题可追溯到具体代码行 |

---

## 审查输出格式

### 标准化报告模板

```markdown
# 对抗性审查报告

## 元信息
- **被审查内容**: [文件/代码片段]
- **审查者模型**: Codex-4.6
- **审查日期**: 2026-03-31
- **审查轮次**: 第2轮

## 严重问题 (Blockers)
| # | Lens | 问题 | 位置 | 建议修复 |
|---|------|------|------|---------|
| 1 | Skeptic | 未处理空指针 | L42 | 添加null检查 |
| 2 | Architect | 循环依赖 | L88-95 | 引入接口解耦 |

## 改进建议 (Suggestions)
| # | Lens | 建议 | 优先级 |
|---|------|------|--------|
| 1 | Minimalist | 提取重复逻辑到函数 | P2 |
| 2 | Architect | 考虑使用策略模式 | P3 |

## 疑问澄清 (Questions)
1. 这个阈值参数是如何确定的?
2. 异常情况下的回退策略是什么?

## 正面确认 (Confirmations)
- ✅ 错误处理覆盖全面
- ✅ 命名清晰易懂

## 总体评估
- [ ] 通过 (无阻塞问题)
- [ ] 有条件通过 (小问题需后续修复)
- [x] 需修改 (存在阻塞问题)
```

---

## 实践模式

### 模式1: 代码审查Skill

```yaml
skill:
  name: "adversarial-code-review"
  trigger: "/review-code"

  workflow:
    1. 接收代码片段
    2. 使用Claude生成初始审查 (Skeptic lens)
    3. 使用Codex进行对抗审查 (Architect + Minimalist lens)
    4. 汇总冲突点
    5. 生成统一报告
    6. 返回给开发者
```

### 模式2: 文档审查Skill

```yaml
skill:
  name: "adversarial-doc-review"
  trigger: "/review-doc"

  workflow:
    1. 接收文档草稿
    2. Claude审查: 结构完整性、逻辑连贯性
    3. Codex审查: 技术准确性、示例可运行性
    4. 交叉验证发现的不一致
    5. 生成修订建议
```

### 模式3: 设计审查Skill

```yaml
skill:
  name: "adversarial-design-review"
  trigger: "/review-design"

  workflow:
    1. 接收设计文档/架构图
    2. 多模型并行审查不同维度:
       - Claude: 用户体验、交互流程
       - Codex: 实现可行性、性能影响
       - GPT-4: 竞品对比、创新度
    3. 综合多维度反馈
```

---

## Skill实现规范 (Adversarial Review Skill)

基于poteto开发的对抗性审查Skill的具体实现细节：

### 硬约束

> "Reviewers MUST run via the opposite model's CLI (`codex exec` or `claude -p`). Do NOT use subagents, the Agent tool, or any internal delegation mechanism as reviewers — those run on *your own* model, which defeats the purpose."

审查者**必须**通过对模型的CLI运行，禁止使用subagents或内部委托机制。

### 审查规模与审查者数量

| 规模 | 阈值 | 审查者 |
|------|------|--------|
| Small | <50行, 1-2文件 | 1 (Skeptic) |
| Medium | 50-200行, 3-5文件 | 2 (Skeptic + Architect) |
| Large | 200+行 或 5+文件 | 3 (Skeptic + Architect + Minimalist) |

### 模型检测与审查者生成

**如果是Claude** → 通过`codex exec`生成Codex审查者：
```sh
codex exec --skip-git-repo-check -o "$REVIEW_DIR/skeptic.md" "prompt" 2>/dev/null
```
- 使用`--profile edit`仅在审查者需要运行测试时
- 默认只读模式
- `run_in_background: true`，通过`TaskOutput`监控，`block: true, timeout: 600000`

**如果是Codex** → 通过`claude` CLI生成Claude审查者：
```sh
claude -p "prompt" > "$REVIEW_DIR/skeptic.md" 2>/dev/null
```
- `run_in_background: true`

输出文件命名：`skeptic.md`, `architect.md`, `minimalist.md`

### 审查者提示词模板结构

每个审查者接收的单一提示词包含：
1. 明确意图（从第2步确定）
2. 分配的视角（`references/reviewer-lenses.md`全文）
3. 相关的brain原则（文件内容，非摘要）
4. 待审查的代码或diff
5. 指令："You are an adversarial reviewer. Your job is to find real problems, not validate the work. Be specific — cite files, lines, and concrete failure scenarios. Rate each finding: high (blocks ship), medium (should fix), low (worth noting). Write findings as a numbered markdown list to your output file."

所有审查者**并行生成**。

### 裁决合成与验证

在读取审查者输出前，记录使用的CLI并确认输出文件存在：
```sh
echo "reviewer_cli=codex|claude"
ls "$REVIEW_DIR"/*.md
```

如有输出文件缺失或为空，在裁决中注明失败——不静默跳过。

### 裁决输出格式

```markdown
## Intent
<作者试图实现的目标>

## Verdict: PASS | CONTESTED | REJECT
<一行摘要>

## Findings
<编号列表，按严重度排序（high → medium → low）>

对于每个发现：
- **[severity]** 描述，含file:line引用
- Lens: 哪个审查者提出的
- Principle: 映射到哪个brain原则
- Recommendation: 具体行动，非模糊建议

## What Went Well
<审查者无问题的1-3件事——肯定好的工作>
```

### 裁决逻辑

| 裁决 | 条件 |
|------|------|
| **PASS** | 无high-severity发现 |
| **CONTESTED** | 有high-severity发现但审查者间有分歧 |
| **REJECT** | 有high-severity发现且审查者达成共识 |

### 主导判断 (Lead Judgment)

合成审查者输出后，应用自己的判断。使用明确意图和brain原则作为框架，说明接受和拒绝哪些发现及其原因。指出假阳性、过度延伸、将风格误认为实质的发现。

追加到裁决：
```markdown
## Lead Judgment
<对每个发现：接受或拒绝及单行理由>
```

### 参考链接

- Skill页面: https://skills.sh/poteto/noodle/adversarial-review
- GitHub: https://github.com/poteto/noodle

---

## 冲突处理

### 当模型意见不一致时

**场景**: Claude认为应该添加抽象层，Codex认为过度设计

**处理流程**:
```
1. 记录冲突
   └── 具体化分歧点 (哪个抽象层? 什么情况下过度?)

2. 引入第三模型仲裁 (如Gemini)
   └── 提供两个观点，要求分析各自的适用场景

3. 场景化决策
   └── "如果这个模块未来会扩展 → 采纳Claude"
   └── "如果这是稳定的核心功能 → 采纳Codex"

4. 记录决策理由
   └── 为什么在这个场景下选择这个观点
```

---

## 效率优化

### 渐进式审查

**分层审查策略**:
```
Layer 1: 自动化检查 (工具)
├── 语法检查 (linter)
├── 静态分析 (type checker)
└── 安全扫描
       ↓ (通过后)

Layer 2: 轻量模型审查 (Haiku/快速模型)
├── 明显问题筛查
└── 快速反馈循环
       ↓ (发现问题)

Layer 3: 深度对抗审查 (Claude + Codex)
├── 架构审查
├── 边界情况分析
└── 综合评估
```

**效果**: 80%的明显问题在Layer 1-2被发现，Layer 3专注复杂问题

---

## 关联概念

- [[Brain-Principles]] — 大脑原则设计模式
- [[Agent-Evaluation]] — Agent评估方法论
- [[Quality-Assurance]] — 质量保证体系
- [[Cross-Validation]] — 交叉验证方法
- [[Multi-Model-Systems]] — 多模型系统设计
- [[Code-Review]] — 代码审查最佳实践
- [[LLM-as-Judge]] — LLM评估模式

---

## 来源与扩展阅读

- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-02_Adversarial_Review_Skill_深度解读]] — 对抗性审查Skill设计与实践
- [[../../20-Areas/AI-Research/Topics/2026-03/2026-03-29_Building_a_better_Bugbot_Cursor_深度解读]] — Cursor Bugbot的对抗性设计

---

## 标签

#evergreen #Adversarial-Review #Code-Review #Multi-Model #Quality-Assurance #Skeptic-Lens #Architect-Lens #Minimalist-Lens
