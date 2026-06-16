# distinctive-ui-design

> A Cursor Agent Skill for designing distinctive UI that avoids the generic "AI template" look —
> across web, iOS/SwiftUI, Android/Compose, and Flutter.
>
> 一个 Cursor Agent Skill，用于做出**没有"AI 模板味"的界面设计**，覆盖 web、iOS/SwiftUI、
> Android/Compose 和 Flutter。

---

## English

### What it does

Without explicit aesthetic direction, AI converges to the "safest", highest-frequency choices in
its training data — Inter fonts, purple-on-white gradients, centered heroes, three identical
feature cards. This skill takes those decisions back by making them explicitly, and extends the
approach to native platforms (not just web).

It gives the agent:

- **A universal method** (4 moves): lock one bold aesthetic direction → forbid each platform's
  "AI default look" by name → one dominant color + one sharp accent → spend the whole motion
  budget on one high-impact moment.
- **A reusable fill-in-the-blank prompt template.**
- **Per-platform playbooks**: the exact "AI default look" to forbid and the native superpowers to
  use (haptics, native TTS, ShareLink, Canvas particles, …) for web / iOS / Android / Flutter.
- **A propose-then-confirm policy**: the agent proposes 2-3 candidate directions for you to pick,
  rather than silently auto-committing.
- **A self-check gate** run before delivering.

### Install

Copy the whole `distinctive-ui-design/` folder into one of:

| Scope | Path |
|---|---|
| Personal (all your projects) | `~/.cursor/skills/distinctive-ui-design/` |
| Project (shared with the repo) | `<repo>/.cursor/skills/distinctive-ui-design/` |

The folder name must match the `name:` in `SKILL.md`. No build step — it loads automatically.

### When it triggers

When you ask for a page/app/screen/component that should look better, more modern, or less
"AI-generated"; when adapting a web design to native iOS/Android; when asking how to prompt AI for
good UI; or when you mention 模板味 / AI 味 / 好看 / 现代 / distinctive design / native UI.

### Files

```
distinctive-ui-design/
├── SKILL.md              # Main instructions (loaded first)
├── platform-playbooks.md # Detailed per-platform negative lists + example prompts
└── README.md             # This file
```

### Relationship to frontend-design

This skill is self-sufficient, including for web. If Cursor's `frontend-design` skill is also
installed, it adds deeper web aesthetics guidance and complements this one. If it is absent,
nothing breaks.

---

## 中文

### 这个 skill 解决什么

没有明确的审美指令时，AI 会收敛到训练数据里"最安全"、最高频的那套——Inter 字体、紫渐变白底、
居中英雄区、三张一模一样的特性卡，也就是所谓"AI 模板味"。这个 skill 把这些审美决策**提前在
提示词里替你做掉**，并把这套方法从 web 扩展到原生平台。

它给 agent 提供：

- **一套通用方法（四个动作）**：锁定一个鲜明且极端的美学方向 → 按名禁用该平台的"AI 默认味" →
  一个主色压倒 + 一个尖锐强调色 → 把全部动效预算砸在一个高光时刻。
- **一份填空式可复用提示词模板。**
- **各平台 playbook**：web / iOS / Android / Flutter 各自"要禁用的 AI 默认味"和"该用的原生超能力"
  （触感、原生 TTS、ShareLink、Canvas 粒子……）。
- **先提案再做的策略**：agent 会先给你 2-3 个候选方向让你选，而不是闷头自己定。
- **交付前自检清单**：做完回头逐条验，不过就先修。

### 安装

把整个 `distinctive-ui-design/` 文件夹放进下面任一目录：

| 范围 | 路径 |
|---|---|
| 个人（所有项目可用） | `~/.cursor/skills/distinctive-ui-design/` |
| 项目（随仓库共享给团队） | `<仓库>/.cursor/skills/distinctive-ui-design/` |

文件夹名必须和 `SKILL.md` 里的 `name:` 一致。无需构建，自动加载。

### 何时触发

当你要做一个页面/应用/界面/组件，希望它更好看、更现代、不那么"像 AI 做的"；当你要把 web 设计
适配成原生 iOS/Android；当你问"怎么给 AI 提示词才能做出好看的 UI"；或当你提到
模板味 / AI 味 / 好看 / 现代 / distinctive design / native UI 时。

### 文件说明

```
distinctive-ui-design/
├── SKILL.md              # 主指令（最先加载）
├── platform-playbooks.md # 各平台详细负面清单 + 示例提示词
└── README.md             # 本文件
```

### 与 frontend-design 的关系

本 skill 自给自足（web 也不例外）。如果同时装了 Cursor 的 `frontend-design` skill，它会补充更深的
web 美学指导、与本 skill 互补；不装也完全不影响使用。

---

## License

MIT
