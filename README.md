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
- 第三方登录接到一半才发现还要接 Apple 登录

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
  开工 ✦ ◄─────────────────────────────┤         ▼
                                        │    上线 ✦
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
                    │              ├─ 数据安全   (data-safety-review)
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
- Discovering you need Apple Login only after you've already built Google Login
- Missing a required App Store config the night before submission

小K酱 is an AI development companion that helps you clear these landmines before you step on them.

---

## Three Entry Points

```
A. New Project   →  Start from scratch, generate CLAUDE.md, lock decisions before coding
B. In Dev        →  Describe what's wrong, KK auto-diagnoses and handles it
C. Pre-Launch    →  Walk through the App Store checklist item by item
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

---

## Support ⭐

Found it useful? Hit the Star button to help others discover it.

Have feedback? → [Open an Issue](https://github.com/kellyvai/love-kk-ios-ai-dev/issues/new/choose)
