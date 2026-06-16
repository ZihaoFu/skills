---
name: distinctive-ui-design
description: >-
  Design distinctive UI that avoids the generic "AI template" look across web, iOS/SwiftUI,
  Android/Compose, and Flutter. Reusable method: lock a bold aesthetic direction, forbid each
  platform's "AI default look" by name (e.g. Inter + purple gradient on web; SF Pro + system blue +
  List/Form on iOS), concentrate motion on one high-impact moment, and use native capabilities
  (haptics, native TTS, ShareLink, Canvas particles). Use when the user wants a page/app/screen/
  component to look better, more modern, or less "AI-generated"; when adapting a web design to
  native iOS/Android; when asking how to prompt AI for good UI; or mentions 模板味 / AI 味 / 好看 /
  现代 / distinctive design / native UI. Complements frontend-design by extending it to native and
  cross-platform.
---

# Distinctive UI Design (Cross-Platform)

Make UI that does not look AI-generated, on any platform. This skill is **self-sufficient on its
own** (including for web — see the Web aesthetics essentials in `platform-playbooks.md`). If the
`frontend-design` skill is also installed, it adds deeper web aesthetics guidance and complements
this one; if it is absent, nothing breaks — use this skill's own content. The added value here is
(1) a reusable prompt method and (2) per-platform negative lists + native capabilities so the
method works on iOS/Android/Flutter, not just web.

## Why AI output looks generic

Without explicit aesthetic direction, models converge to the highest-frequency, "safest" choices
in their training data. The fix is always the same: **take the aesthetic decisions away from the
model by making them explicitly in the prompt — especially the ones it will lazily converge on.**

## Direction policy: propose, then confirm

Before locking a direction, **infer 2-3 candidate aesthetic directions from the product's tone and
propose them to the user in one line each** (e.g. "水墨留白 / 极简留白 / 复古印刷"), then let the
user pick or redirect. Only skip this and auto-pick when the user already named a style, or the
choice is trivial. Aesthetic is subjective and this step is nearly free — do not auto-commit to a
look without offering the choice first.

## The universal method (platform-agnostic)

Apply these four moves every time. They transfer across all platforms:

1. **Lock one bold, extreme aesthetic direction** (the one the user picked above) before any code.
   Pick an extreme (brutal minimal, maximalist, retro-futuristic, ink-wash/国风, editorial, luxury,
   etc.) and state the design intent first. This denies the model room to converge on a template.
2. **Forbid by name** — give a negative list of the platform's "AI default look" choices (see
   per-platform lists below). Negative lists outperform positive requests.
3. **One dominant color + one sharp accent.** Cures "evenly-distributed palette, gradients everywhere".
4. **Spend the entire motion budget on ONE high-impact moment** (one orchestrated reveal with
   staggered entrance) instead of scattered micro-interactions.

Plus one **workflow technique** (not in the prompt text, but decisive):
**First produce only the design system + one signature component; confirm; then build the rest.**
Iterate one axis at a time ("this pass only changes type and color"). Feed references, not adjectives.

## Reusable prompt template (fill in the blanks)

```
帮我做 [target]。写代码前先定一个鲜明且极端的美学方向并简述设计意图,再实现。

【美学方向】[一个极端方向,如:水墨留白 / 粗野主义 / 杂志编辑风 ...] + 一处极致的[高光时刻]。
【硬约束——避开 [平台] 默认味】
1. 字体:禁用 [平台默认字体清单];用 [有个性的 display 字体] + [精致正文字体] 配对。
2. 配色:禁用 [平台默认强调色/紫渐变白底];主色 [X] 压倒 + 强调色 [Y] 只在关键处。
3. 布局/控件:禁用 [平台默认控件/布局,见负面清单];要 [不对称/留白/特色版式]。
4. 背景:不要纯色,叠加 [质感:噪点/纹理/墨晕/渐变网格]。
5. 动效:不要零散特效,全部集中到 [高光时刻],错峰入场。
6. [平台原生能力:见下表,写进高光时刻]。
【交付】先产出设计系统(色板+字体+一个标志性组件)和可预览示例,确认后再铺全页。
```

## Per-platform quick reference

The single most important platform-specific edit is **the negative list** (what "AI default look"
means on that platform) and **the native capabilities** worth putting in the high-impact moment.

| Platform | Forbid (AI default look) | Native superpowers to use |
|---|---|---|
| **Web** | Inter/Roboto/Arial/system fonts, Space Grotesk; purple gradient on white; centered hero + 3-col feature cards; default rounded+shadow boxes | CSS keyframes, scroll-trigger, SVG/Canvas texture |
| **iOS / SwiftUI** | SF Pro as main type; system blue / default tint; List/Form/default NavigationStack; stock SF Symbols as hero; ultraThinMaterial on everything | Haptics (CoreHaptics), AVSpeechSynthesizer, ShareLink + ImageRenderer, Canvas+TimelineView particles, matchedGeometryEffect |
| **Android / Compose** | Default Material 3 baseline theme; Roboto; default dynamic-color purple; stock Material components untouched | Haptic feedback, MotionLayout/animate*AsState, Canvas particles, predictive-back |
| **Flutter** | Default Material/Cupertino widgets unstyled; Roboto; ThemeData defaults | Custom painters, implicit/explicit animations, Hero transitions, haptic feedback |

**Cross-platform native must-dos:** respect platform conventions for navigation, gestures, safe
areas, minimum touch target (44pt iOS / 48dp Android), Dynamic Type / font scaling, dark mode
(use semantic color assets, never hardcode), and accessibility (VoiceOver/TalkBack). Be a good
platform citizen in *interaction*; be distinctive in *visual skin*.

For full per-platform playbooks (detailed negative lists, native API specifics, and filled-in
example prompts for each platform), see [platform-playbooks.md](platform-playbooks.md).

## Self-check before delivering

After building, verify the result against this gate. If any item fails, fix it before delivering:

- [ ] **No negative-list items present** — none of this platform's "AI default look" choices slipped in.
- [ ] **Distinctive type** — no default/generic font as the main face; display + body are paired.
- [ ] **One dominant color + one sharp accent** — not an evenly-distributed palette or gradients everywhere.
- [ ] **Motion concentrated** — one orchestrated high-impact moment, not scattered micro-interactions.
- [ ] **Background has atmosphere** — texture/noise/gradient/depth, not a flat solid fill.
- [ ] **Native capability used** (native targets) — at least one platform superpower in the key moment.
- [ ] **Good platform citizen** — safe areas, touch targets, dynamic type, dark mode, accessibility.

## Adapting between platforms

When porting a design to a new platform, only two things really change:
1. Swap the **negative list** to that platform's "AI default look".
2. Swap the **native capabilities** woven into the high-impact moment.

The four universal moves and the workflow stay identical.
