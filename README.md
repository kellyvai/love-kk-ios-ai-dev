# 小K酱 · iOS AI 开发防踩坑助理

**love kk - ios ai dev**

> 一个帮没有编程背景的创作者把 App 从想法做到上架的 Claude Code Skill。
> 小K做能做的，只有真正需要你决策的时候才问你。

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License">
  <img src="https://img.shields.io/github/stars/kellyvai/love-kk-ios-ai-dev?style=social" alt="Stars">
  <img src="https://img.shields.io/badge/Claude%20Code-Skill-8A2BE2" alt="Claude Code Skill">
</p>

[English](#english) | 中文

---

## 安装

```bash
npx skills add kellyvai/love-kk-ios-ai-dev@ios-ai-dev
```

依赖 skill（本 skill 在以下节点会调用它们，需单独安装）：

```bash
# A7 设计阶段 + B1 设计问题
npx skills add qiaomu/qiaomu-design-advisor@qiaomu-design-advisor

# C2 合规扫描
npx skills add safaiyeh/app-store-review@app-store-review
```

启动：

```
/ios-ai-dev
```

---

## 这个 Skill 能做什么

### 四个流程阶段

如果你是一个有产品想法、但不是程序员的创作者，你大概率会踩这些坑：

**新项目启动（A 流程）**
- 开工前没想清楚，做到一半发现方向不对
- CLAUDE.md 没有，AI 三天后开始犯低级错误
- 第三方登录接到一半才发现还要补一个符合审核指南 4.8 的登录选项（通常是 Apple 登录）

**开发中（B 流程）**
- Prompt 写完效果不稳定，改了又改，前端越来越乱
- 数据流转不清，找不到 bug 在哪一层
- 设计没有统一规范，各个页面风格不一致

**准备上线（C 流程）**
- 上线前才发现缺了某个苹果审核的必要配置
- 权限描述不清，直接被 App Store 拒审
- 支付配置不完整，审核流程卡壳

**质量审查与优化（D 流程）**
- 应用已上线，用户反馈问题多，不知道从哪里开始改
- 想做优化但没有系统的审查方法，改了一处忘了一处
- 需要全面体检应用，但不知道应该检查哪些维度

### 小K 陪你全程完成

小K酱是一个陪你全程的 AI 开发助理，把这些坑提前踩完。特别是新增的 D 流程，能让你：
- 快速诊断具体用户反馈问题
- 深度审查应用的内容、逻辑、体验、安全、代码五个维度
- 生成优先级清晰的优化规划，而不是盲目改进

---

## 四个入口

```
A. 新项目启动    →  从零开始，生成 CLAUDE.md，开工前全部想清楚
B. 开发中       →  告诉小K哪里不对，小K自动诊断并处理
C. 准备上线     →  逐项过 App Store 审核清单，确保顺利过审
D. 质量审查与优化 →  应用成型后，全面体检或解决用户反馈问题
```

---

## 流程图

```
┌─────────────────────────────────────────────────────┐
│                   /ios-ai-dev 启动                   │
└──────────┬────────────────────────────────────────┬─┘
           │                                        │
    ┌──────┴─────────────────────────────┐         │
    │                                    │         │
    ▼                                    ▼         ▼
A. 新项目启动                        B. 开发中   C. 准备上线
    │                                    │         │
    ├─ A0 收集项目信息                    │         │
    ├─ A1 生成 CLAUDE.md                  │         │
    ├─ A2 产品定义对齐                    ├─ B1 自动诊断分类
    ├─ A2.5 AI 设计协作方法论             │         │
    ├─ A3 产品逻辑文档                    ├─ 代码bug → debug
    ├─ A4 技术选型锁定                    ├─ 上下文丢 → CLAUDE.md补全
    ├─ A5 登录合规检查                    ├─ prompt偏 → prompt排查
    ├─ A6 Prompt 架构设计                 ├─ 设计问题 → 设计审查
    ├─ A7 设计审查(/qiaomu)              │         │
    ├─ A8 Jobs视角审计                    │         ├─ C1 逐项清单确认
    │                                    │         ├─ C2 调用 /app-store-review
    ▼                                    │         │
  开工   ◄─────────────────────────────┤         ▼
                                        │    上线
                                        │
                                        ▼
                               D. 质量审查与优化
                                        │
                                ┌───────┴──────────┐
                                │                  │
                                ▼                  ▼
                           D1 快速诊断         D2 深度审查
                           (具体问题)         (全面体检)
                                │                  │
                    ┌───────────┴──────────┐      │
                    │                      │      │
                    ▼                      ▼      ▼
            问题诊断与修复            5层并行审查
                    │              ├─ 内容准确性 (content-accuracy-audit.md)
                    │              ├─ 业务逻辑   (logic-integrity-audit.md)
                    │              ├─ 用户体验   (ux-evaluation-audit.md)
                    │              ├─ 数据安全   (data-safety-audit.md)
                    │              ├─ 代码质量   (code-quality-audit.md)
                    │              │
                    │              ▼
                    │         生成审查报告
                    │              │
                    │         用户确认优化规划
                    │              │
                    └──────────┬───┘
                               │
                        优化实施规划
                               │
                    ┌──────────┼──────────┐
                    ▼          ▼          ▼
               P0修复    P1优化    P2增强
                    │          │          │
                    └──────────┴──────────┘
                               │
                        实施完成后 → 回到 C(上线前检查)
```

---

## 文件结构

```
ios-ai-dev/
├── SKILL.md                           # 主流程编排（A/B/C/D 四大流程）
├── workflows/
│   └── QUALITY_AUDIT_WORKFLOW.md      # D流程详细定义（D0/D1/D2）
├── prompts/
│   ├── product-design.md              # 产品设计框架（A2 调用）
│   ├── ai-design-collab.md            # AI 设计协作方法论（A2.5 调用）
│   ├── prompt-architecture.md         # AI Prompt 架构模板（A6 调用）
│   ├── claude-md-template.md          # CLAUDE.md 标准模板（A1 调用）
│   ├── content-accuracy-audit.md      # 内容准确性审查框架（D2 调用）
│   ├── logic-integrity-audit.md       # 业务逻辑审查框架（D2 调用）
│   ├── ux-evaluation-audit.md         # 用户体验评估框架（D2 调用）
│   ├── data-safety-audit.md           # 数据有效性与安全审查框架（D2 调用）
│   └── code-quality-audit.md          # 代码质量审查框架（D2 调用）
└── refs/
    └── appstore-checklist.md          # App Store 详细审核清单（C1 调用）
```

---

## 核心原则

小K的底线，不会因为主人催就跳过：

1. CLAUDE.md 是地基，没有它 AI 三天后开始犯低级错误
2. 功能定义开工前对齐，成功标准没定义清楚就开工，做完方向是错的
3. 格式约定开工前定死，中途改格式的代价是全量兼容补丁
4. Prompt 先定输出格式，再写规则，规则写进文档不靠 AI 猜
5. 门槛检查设成 Step Zero，整体不符合条件就不做后续分析
6. AI 输出值直接驱动前端行为，不在前端再加一层翻译逻辑
7. Prompt 和前端 parser 必须同步修改，单独改一边必然崩
8. 前端加兜底校验，不能完全依赖 prompt 保证正确性
9. 异步操作必须有 finally 释放锁，否则第一次之后永久失效
10. 同一组件只渲染一次，双重渲染是隐性 bug 的温床
11. 第三方登录开工前配置好，中途接入成本翻倍
12. 设计先行，中途改设计比改代码便宜，改代码比上线后改便宜
13. 第一天就找真实用户内测，做完再改比做到一半改贵 10 倍
14. 技术细节不确定就搜官方文档，不用训练数据猜

---

## 实战工具箱

下面是作者在真实 App 开发中反复用到的搭配和习惯。它们不属于本 Skill 的必装依赖，按需取用。其中的命令和文件名（如 `review:gate`、`AGENT_SHARED_CONTEXT.md`）是作者项目里的示例，本仓库不提供，需要的话照思路自行实现。

### 设计与视觉层

| 场景 | 常用 Skill |
|------|-----------|
| UI 规范、可访问性、移动端体验 | ui-ux-pro-max、mobile-app-design |
| HTML 高保真原型、设计变体、设计评审 | huashu-design |
| 动效、手势、转场 | ui-animation |
| 视觉质感升级、旧页面翻新 | high-end-visual-design、redesign-existing-projects |

这一层对应 B1 的设计检查。顺序建议：先用 mobile-app-design 定规范，再用 huashu-design 出原型，最后用 ui-animation 补动效。

### 发布前质量门

在 D 流程的五维审查之外，加一道机器可判定的门，改完代码先跑它，再做人工审查：

```bash
npm run review:gate:fast   # 迭代时用，跳过测试
npm run review:gate        # 提交前用：类型 + lint + 守卫 + 测试
```

- 老项目通常已有一批历史类型错误，不要求清零，用"棘轮"：本次改动过的文件不能更糟，基线只降不升。
- 通过 gate 不等于审查通过，它只覆盖能机械判定的部分。
- 涉及钱和积分、登录、数据库迁移、原生与发版配置、AI Prompt、共享数据定义时，由人最终确认，不让 AI 自行宣布通过。
- 汇报时贴真实命令输出，并明确列出"没验证的部分"，不写"待真机回归"这类没做过的事。

### 多 Agent 共用同一个工作树

同时开多个 AI 会话改同一个项目时：

- 只 `git add` 自己改的文件，不用 `git add -A`
- 不用 `git checkout -- .`、`git stash`、`git reset --hard`，它们会吃掉别的会话的未提交改动

### 项目上下文文件

- `AGENT_SHARED_CONTEXT.md`：只放当前活跃状态，每次改完必须更新（日期、谁做的、目标、改了什么、怎么验证、遗留项）。只保留最近 10 条，旧的归档，启动时不读归档。
- 发版时在里面额外记录：渠道、公开版本号、构建号、状态与日期、关键改动、验证、后续。
- `PRODUCT_MAP.md`：功能与内容结构的活地图。改功能、内容结构、页面入口前先读，并抽查代码；以代码为准，发现不一致就地修图。

---

## 鸣谢

本 Skill 在以下开源作品的基础上整合工作流节点：

| Skill | 作者 | 调用节点 | 链接 |
|-------|------|----------|------|
| qiaomu-design-advisor | [@qiaomu](https://github.com/qiaomu) | A7 设计阶段 / B1 设计问题 | [repo](https://github.com/qiaomu/qiaomu-design-advisor) |
| app-store-review | [@safaiyeh](https://github.com/safaiyeh) | C2 合规扫描 | [repo](https://github.com/safaiyeh/app-store-review) |
| apple-hig-designer（可选） | — | B1 iOS 规范检查 | 暂无公开来源，缺失时使用内置检查 |
| steve-jobs-perspective（可选） | — | A8 Jobs 视角审计 | 暂无公开来源，缺失时使用内置三问自查 |

---

## License

MIT

---

## 支持这个 Skill ⭐

觉得有用的话，右上角点个 Star，让更多人看到 💪

有建议或问题 → [提 Issue](https://github.com/kellyvai/love-kk-ios-ai-dev/issues/new/choose)

---

<a name="english"></a>

# 小K酱 · iOS AI Dev Pitfall-Prevention Assistant

**love kk - ios ai dev**

> A Claude Code Skill that guides non-technical creators from idea to App Store.
> KK handles what she can. She only asks you when a real decision is needed.

---

## Installation

```bash
npx skills add kellyvai/love-kk-ios-ai-dev@ios-ai-dev
```

Dependency skills (called at specific workflow nodes):

```bash
npx skills add qiaomu/qiaomu-design-advisor@qiaomu-design-advisor
npx skills add safaiyeh/app-store-review@app-store-review
```

Launch: `/ios-ai-dev`

---

## What This Skill Does

If you're a creator with a product idea but no programming background, you'll likely hit these walls:

- Starting before you're clear on direction, pivoting halfway through
- No CLAUDE.md, so the AI starts making dumb mistakes after a few sessions
- Prompt instability — keeps changing, frontend falls out of sync
- Discovering you need an equivalent login option (usually Sign in with Apple, per guideline 4.8) only after you've already built Google Login
- Missing a required App Store config the night before submission
- After launch, lots of user feedback but no idea where to start fixing, or no systematic way to audit the app

小K酱 is an AI development companion that helps you clear these landmines before you step on them.

---

## Four Entry Points

```
A. New Project   →  Start from scratch, generate CLAUDE.md, lock decisions before coding
B. In Dev        →  Describe what's wrong, KK auto-diagnoses and handles it
C. Pre-Launch    →  Walk through the App Store checklist item by item
D. Quality Audit →  After it takes shape, full health check or fix user-reported issues
```

---

## D Flow: Quality Audit & Optimization

Entry point D0 asks one question: do you have a specific problem, or do you want a full health check?

- **D1 Quick Diagnosis** (a specific problem): KK collects the symptom (error text, what is wrong, expected behavior, since when), classifies it, and routes it. Code bug goes to the B1 debug flow, content problem to the content audit, logic error to the logic analysis, design or UX problem to the design review. Then a fix plan is produced.
- **D2 Deep Audit** (full health check): KK collects basic app info, then runs five audits in parallel:
  1. Content accuracy (`prompts/content-accuracy-audit.md`)
  2. Business logic (`prompts/logic-integrity-audit.md`)
  3. User experience (`prompts/ux-evaluation-audit.md`)
  4. Data validity and safety (`prompts/data-safety-audit.md`)
  5. Code and architecture (`prompts/code-quality-audit.md`)

  The result is one report with critical, important and optional issues. You confirm or adjust the plan (agree, reprioritize, add items, or skip), then KK writes a phased roadmap: P0 fixes, P1 optimizations, P2 enhancements. Every item states the problem, root cause, fix, how to verify, and an effort estimate. After implementation, go back to C for the pre-launch check.

D principles: KK never replaces your decision on priorities; every issue is concrete (what, why, how to fix); priorities are clear; effort is estimable; every change has a verification step.

Full definition: `workflows/QUALITY_AUDIT_WORKFLOW.md`.

---

## Flowchart

```
┌─────────────────────────────────────────────────────┐
│                  /ios-ai-dev launch                  │
└──────────┬────────────────────────────────────────┬─┘
           │                                        │
    ┌──────┴─────────────────────────────┐         │
    │                                    │         │
    ▼                                    ▼         ▼
A. New Project                      B. In Dev   C. Pre-Launch
    │                                    │         │
    ├─ A0 Collect project info           │         │
    ├─ A1 Generate CLAUDE.md             │         │
    ├─ A2 Align product definition       ├─ B1 Auto-diagnose & classify
    ├─ A2.5 AI design collab method      │         │
    ├─ A3 Product logic doc              ├─ Code bug → debug
    ├─ A4 Lock tech stack                ├─ Lost context → fix CLAUDE.md
    ├─ A5 Login compliance check         ├─ Prompt drift → prompt review
    ├─ A6 Prompt architecture            ├─ Design issue → design review
    ├─ A7 Design review (/qiaomu)        │         │
    ├─ A8 Jobs-perspective audit         │         ├─ C1 Checklist, item by item
    │                                    │         ├─ C2 Run /app-store-review
    ▼                                    │         │
  Start building ◄───────────────────────┤         ▼
                                         │      Launch
                                         ▼
                              D. Quality Audit & Optimization
                                         │
                                 ┌───────┴──────────┐
                                 │                  │
                                 ▼                  ▼
                          D1 Quick Diagnosis   D2 Deep Audit
                          (specific issue)     (full health check)
                                 │                  │
                     ┌───────────┴─────────┐        │
                     │                     │        │
                     ▼                     ▼        ▼
              Diagnose & fix        5 parallel audits
                     │              ├─ Content accuracy (content-accuracy-audit.md)
                     │              ├─ Business logic   (logic-integrity-audit.md)
                     │              ├─ User experience  (ux-evaluation-audit.md)
                     │              ├─ Data safety      (data-safety-audit.md)
                     │              ├─ Code quality     (code-quality-audit.md)
                     │              │
                     │              ▼
                     │         Audit report
                     │              │
                     │         You confirm the plan
                     │              │
                     └──────────┬───┘
                                │
                        Optimization roadmap
                                │
                     ┌──────────┼──────────┐
                     ▼          ▼          ▼
                 P0 fixes   P1 optimize  P2 enhance
                     │          │          │
                     └──────────┴──────────┘
                                │
                  After implementation → back to C (pre-launch check)
```

---

## File Structure

```
ios-ai-dev/
├── SKILL.md                           # Main workflow orchestration (A/B/C/D)
├── workflows/
│   └── QUALITY_AUDIT_WORKFLOW.md      # D flow definition (D0/D1/D2)
├── prompts/
│   ├── product-design.md              # Product design framework (A2)
│   ├── ai-design-collab.md            # AI design collaboration method (A2.5)
│   ├── prompt-architecture.md         # AI Prompt architecture template (A6)
│   ├── claude-md-template.md          # CLAUDE.md standard template (A1)
│   ├── content-accuracy-audit.md      # Content accuracy audit (D2)
│   ├── logic-integrity-audit.md       # Business logic audit (D2)
│   ├── ux-evaluation-audit.md         # UX evaluation audit (D2)
│   ├── data-safety-audit.md           # Data validity & safety audit (D2)
│   └── code-quality-audit.md          # Code quality audit (D2)
└── refs/
    └── appstore-checklist.md          # Detailed App Store checklist (C1)
```

---

## Core Principles

KK's bottom line. She will not skip these even if you rush her:

1. CLAUDE.md is the foundation. Without it the AI starts making dumb mistakes within days
2. Align feature definitions before coding. Undefined success criteria means the wrong thing gets built
3. Lock format conventions before coding. Changing a format midway costs a full compatibility patch
4. Define the Prompt output format first, then the rules. Put rules in docs, never rely on the AI guessing
5. Make the gate check "Step Zero". If the input fails the entry condition, skip all later analysis
6. When an AI output value drives frontend behavior, do not add a translation layer in the frontend
7. Change the Prompt and the frontend parser together. Changing only one side will break
8. Add fallback validation in the frontend. Never rely entirely on the prompt for correctness
9. Every async operation must release its lock in `finally`, or it stops working after the first run
10. Render each component once. Double rendering breeds hidden bugs
11. Set up third-party login before you start. Adding it midway doubles the cost
12. Design first. Changing design midway is cheaper than changing code, which is cheaper than changing after launch
13. Get real testers on day one. Fixing after you finish costs 10x more than fixing midway
14. If a technical detail is uncertain, search the official docs. Do not guess from training data

---

## Field Toolbox

Combinations and habits the author reuses across real app builds. Optional, not required dependencies. Commands and file names such as `review:gate` and `AGENT_SHARED_CONTEXT.md` are examples from the author's own project and are not shipped here; implement the idea yourself if you want it.

- **Design layer**: ui-ux-pro-max and mobile-app-design for UI rules, huashu-design for HTML hi-fi prototypes and design review, ui-animation for motion, high-end-visual-design and redesign-existing-projects for polish and refresh. Pairs with B1.
- **Pre-release gate**: a mechanical gate (type check ratchet, lint ratchet, guards, tests) runs before human review. Touched files must not get worse. Passing the gate is not review approval. Money, auth, migrations, release config and AI prompts always get a human sign-off. Report real command output and list what was not verified.
- **Shared working tree**: with several AI sessions on one repo, only `git add` your own files. Never `git add -A`, `git stash`, `git reset --hard` or `git checkout -- .`.
- **Context files**: keep a compact `AGENT_SHARED_CONTEXT.md` (latest 10 entries, older ones archived) and a living `PRODUCT_MAP.md` (code wins over the map).

---

## Credits

This skill integrates workflow nodes from the following open-source works:

| Skill | Author | Used At | Link |
|-------|--------|---------|------|
| qiaomu-design-advisor | [@qiaomu](https://github.com/qiaomu) | A7 Design / B1 Design Issues | [repo](https://github.com/qiaomu/qiaomu-design-advisor) |
| app-store-review | [@safaiyeh](https://github.com/safaiyeh) | C2 Compliance Scan | [repo](https://github.com/safaiyeh/app-store-review) |
| apple-hig-designer (optional) | — | B1 iOS HIG Check | No public source; built-in checks are used if missing |
| steve-jobs-perspective (optional) | — | A8 Jobs Audit | No public source; built-in three-question check is used if missing |

---

## License

MIT

---

## Support ⭐

Found it useful? Hit the Star button to help others discover it.

Have feedback? → [Open an Issue](https://github.com/kellyvai/love-kk-ios-ai-dev/issues/new/choose)
