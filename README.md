# 小K酱 · iOS AI 开发防踩坑助理

**love kk - ios ai dev**

> 一个帮没有编程背景的创作者把 App 从想法做到上架的 Claude Code Skill。
> 小K做能做的，只有真正需要你决策的时候才问你。

[English](#english) | 中文

---

## 安装

```bash
# 1. 克隆到 Claude Code skills 目录
git clone https://github.com/chen0937662845-bit/love-kk-ios-ai-dev.git \
  ~/.claude/skills/ios-ai-dev

# 2. 安装依赖 skill（本 skill 在以下节点会调用它们）
# qiaomu-design-advisor（A7 设计阶段 + B1 设计问题）
# → https://github.com/qiaomu/qiaomu-design-advisor
#
# app-store-review（C2 合规扫描）
# → https://github.com/safaiyeh/app-store-review
#
# steve-jobs-perspective / apple-hig-designer
# → 单独安装

# 3. 在 Claude Code 中启动
/ios-ai-dev
```

---

## 这个 Skill 能做什么

如果你是一个有产品想法、但不是程序员的创作者，你大概率会踩这些坑：

- 开工前没想清楚，做到一半发现方向不对
- CLAUDE.md 没有，AI 三天后开始犯低级错误
- Prompt 写完效果不稳定，改了又改，前端越来越乱
- 第三方登录接到一半才发现还要接 Apple 登录
- 上线前才发现缺了某个苹果审核的必要配置

小K酱是一个陪你全程的 AI 开发助理，把这些坑提前踩完。

---

## 三个入口

```
A. 新项目启动  →  从零开始，生成 CLAUDE.md，开工前全部想清楚
B. 开发中      →  告诉小K哪里不对，小K自动诊断并处理
C. 准备上线    →  逐项过 App Store 审核清单，确保顺利过审
```

---

## 流程图

```
┌─────────────────────────────────────────────────────┐
│                   /ios-ai-dev 启动                   │
└─────────────────────┬───────────────────────────────┘
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
     A. 新项目     B. 开发中   C. 准备上线
          │           │           │
          ▼           ▼           ▼
   ┌──────────┐  ┌─────────┐  ┌──────────┐
   │ A0 收集  │  │ B1 自动 │  │ C1 逐项  │
   │ 项目信息 │  │ 诊断分类│  │ 清单确认 │
   └────┬─────┘  └────┬────┘  └────┬─────┘
        │             │             │
        ▼             │             ▼
   ┌──────────┐       │       ┌──────────┐
   │ A1 生成  │       │       │ C2 调用  │
   │ CLAUDE.md│       │       │/app-store│
   └────┬─────┘       │       │ -review  │
        │             │       └──────────┘
        ▼             │
   ┌──────────┐  ┌────┴──────────────────────┐
   │ A2 产品  │  │ 代码bug → debug流程        │
   │ 定义对齐 │  │ 边界失控 → CLAUDE.md保护   │
   │(product- │  │ 上下文丢 → CLAUDE.md补全   │
   │design.md)│  │ prompt偏 → prompt排查      │
   └────┬─────┘  │ 联调断层 → 三层debug       │
        │        │ 设计问题 → 设计审查        │
        ▼        └───────────────────────────┘
   ┌──────────┐
   │ A3 产品  │
   │ 逻辑文档 │
   └────┬─────┘
        │
        ▼
   ┌──────────┐
   │ A4 技术  │
   │ 选型锁定 │
   └────┬─────┘
        │
        ▼
   ┌──────────┐
   │ A5 登录  │
   │ 合规检查 │
   └────┬─────┘
        │
        ▼
   ┌──────────┐
   │ A6 Prompt│  ←  使用 prompt-architecture.md 模板
   │ 架构设计 │
   └────┬─────┘
        │
        ▼
   ┌──────────┐
   │ A7 调用  │  ←  /qiaomu-design-advisor
   │ 设计审查 │
   └────┬─────┘
        │
        ▼
   ┌──────────┐
   │ A8 Jobs  │  ←  /steve-jobs-perspective
   │ 视角审计 │
   └────┬─────┘
        │
        ▼
      开工 ✦
```

---

## 文件结构

```
ios-ai-dev/
├── SKILL.md                      # 主流程编排
├── prompts/
│   ├── product-design.md         # 产品设计框架（A2 调用）
│   ├── prompt-architecture.md    # AI Prompt 架构模板（A6 调用）
│   └── claude-md-template.md     # CLAUDE.md 标准模板（A1 调用）
└── refs/
    └── appstore-checklist.md     # App Store 详细审核清单（C1 调用）
```

---

## 安装

```bash
# 1. 克隆到 Claude Code skills 目录
git clone https://github.com/rongjiaqi/love-kk-ios-ai-dev.git \
  ~/.claude/skills/ios-ai-dev

# 2. 安装依赖 skill（本 skill 在以下节点调用它们）
# qiaomu-design-advisor（A7 设计阶段 + B1 设计问题）
# → https://github.com/qiaomu/qiaomu-design-advisor

# steve-jobs-perspective（A8 审计阶段）
# → 单独安装

# apple-hig-designer（B1 iOS 规范检查）
# → 单独安装

# app-store-review（C2 合规扫描）
# → https://github.com/safaiyeh/app-store-review

# 3. 在 Claude Code 中使用
/ios-ai-dev
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

## 鸣谢

本 Skill 在以下开源作品的基础上整合工作流节点：

| Skill | 作者 | 调用节点 | 链接 |
|-------|------|----------|------|
| qiaomu-design-advisor | [@qiaomu](https://github.com/qiaomu) | A7 设计阶段 / B1 设计问题 | [repo](https://github.com/qiaomu/qiaomu-design-advisor) |
| app-store-review | [@safaiyeh](https://github.com/safaiyeh) | C2 合规扫描 | [repo](https://github.com/safaiyeh/app-store-review) |
| apple-hig-designer | — | B1 iOS 规范检查 | — |
| steve-jobs-perspective | — | A8 Jobs 视角审计 | — |

---

## License

MIT

---

---

<a name="english"></a>

# 小K酱 · iOS AI Dev Pitfall-Prevention Assistant

**love kk - ios ai dev**

> A Claude Code Skill that guides non-technical creators from idea to App Store.
> KK handles what she can. She only asks you when a real decision is needed.

---

## Installation

```bash
# 1. Clone into Claude Code skills directory
git clone https://github.com/chen0937662845-bit/love-kk-ios-ai-dev.git \
  ~/.claude/skills/ios-ai-dev

# 2. Install dependency skills
# qiaomu-design-advisor (A7 design + B1 design issues)
# → https://github.com/qiaomu/qiaomu-design-advisor
#
# app-store-review (C2 compliance scan)
# → https://github.com/safaiyeh/app-store-review
#
# steve-jobs-perspective / apple-hig-designer
# → install separately

# 3. Launch in Claude Code
/ios-ai-dev
```

---

## What This Skill Does

If you're a creator with a product idea but no programming background, you'll likely hit these walls:

- Starting before you're clear on direction, pivoting halfway through
- No CLAUDE.md, so the AI starts making dumb mistakes after a few sessions
- Prompt instability — keeps changing, frontend falls out of sync
- Discovering you need Apple Login only after you've already built Google Login
- Missing a required App Store config the night before submission

小K酱 is an AI development companion that helps you clear these landmines before you step on them.

---

## Three Entry Points

```
A. New Project   →  Start from scratch, generate CLAUDE.md, lock decisions before coding
B. In Dev        →  Describe what's wrong, KK auto-diagnoses and handles it
C. Pre-Launch    →  Walk through the App Store checklist item by item
```

---

## How KK Works

KK does the work herself. She only surfaces a decision to you when it's genuinely yours to make — like which IAP naming convention to use (once set, can't change) or whether to add Apple Login now or before launch.

Everything else: she handles, then tells you what she did and asks "does this look right?"

---

## File Structure

```
ios-ai-dev/
├── SKILL.md                      # Main workflow orchestration
├── prompts/
│   ├── product-design.md         # Product design framework (used in A2)
│   ├── prompt-architecture.md    # AI Prompt architecture template (used in A6)
│   └── claude-md-template.md     # CLAUDE.md standard template (used in A1)
└── refs/
    └── appstore-checklist.md     # Detailed App Store review checklist (used in C1)
```

---

## Installation

```bash
# 1. Clone into Claude Code skills directory
git clone https://github.com/rongjiaqi/love-kk-ios-ai-dev.git \
  ~/.claude/skills/ios-ai-dev

# 2. Install dependency skills (called at specific workflow nodes)
# qiaomu-design-advisor (A7 design stage + B1 design issues)
# → https://github.com/qiaomu/qiaomu-design-advisor

# app-store-review (C2 compliance scan)
# → https://github.com/safaiyeh/app-store-review

# steve-jobs-perspective (A8 audit)
# apple-hig-designer (B1 iOS spec check)
# → install separately

# 3. Launch in Claude Code
/ios-ai-dev
```

---

## Credits

This skill integrates workflow nodes from the following open-source works:

| Skill | Author | Used At | Link |
|-------|--------|---------|------|
| qiaomu-design-advisor | [@qiaomu](https://github.com/qiaomu) | A7 Design / B1 Design Issues | [repo](https://github.com/qiaomu/qiaomu-design-advisor) |
| app-store-review | [@safaiyeh](https://github.com/safaiyeh) | C2 Compliance Scan | [repo](https://github.com/safaiyeh/app-store-review) |
| apple-hig-designer | — | B1 iOS HIG Check | — |
| steve-jobs-perspective | — | A8 Jobs Audit | — |

---

## License

MIT
