# Platform Playbooks

Detailed per-platform negative lists, native capabilities, and filled-in example prompts.
Read this when you need specifics beyond the quick-reference table in `SKILL.md`.

---

## Web (HTML/CSS/JS, React, Vue)

**AI default look to forbid:**
- Fonts: Inter, Roboto, Arial, system-ui, and the over-used "fix" Space Grotesk.
- Color: purple/violet gradient on a white background; many soft gradients evenly distributed.
- Layout: centered hero + three equal feature cards; everything in rounded boxes with soft shadow.
- Effects: scattered hover micro-interactions instead of one orchestrated moment.

**Native superpowers:** CSS keyframes + `animation-delay` for staggered reveals; scroll-triggered
reveals; SVG `feTurbulence` noise / Canvas for texture; custom cursors; `mix-blend-mode`.

**Delivery:** single self-contained HTML when it's a demo; otherwise component files. Google Fonts
via `<link>`.

**Web aesthetics essentials (self-contained — use these whether or not `frontend-design` is installed):**
- **Typography:** pair a distinctive display font with a refined body font; avoid generic faces.
  Use CSS variables for the type scale; consider unexpected weights/sizes for hierarchy.
- **Color:** one dominant color + one sharp accent, in CSS variables. Dark or unconventional grounds
  often beat the default white. No timid evenly-distributed palettes.
- **Motion:** prefer CSS-only; one orchestrated page-load reveal with staggered `animation-delay`
  beats scattered hovers. Add a few surprising hover/scroll states.
- **Spatial composition:** asymmetry, overlap, diagonal flow, grid-breaking elements; generous
  negative space OR controlled density. Avoid centered-hero + 3-equal-cards.
- **Backgrounds/texture:** gradient mesh, SVG noise, geometric patterns, layered transparency,
  dramatic shadows, grain overlays — atmosphere over flat solid color.
- Match implementation complexity to the vision: maximalist → elaborate effects; minimal → restraint
  and precise spacing/typography.

**Filled example (国风 ink-wash):**
```
帮我做一个抽卡揭晓页面(纯静态、单文件)。写代码前先定美学方向并简述设计意图。
【美学方向】水墨留白 + 杂志竖排 + 一处极致的揭晓动效。气质安静、克制、高级。
【硬约束】
1. 字体:禁用 Inter/Roboto/系统字体/Space Grotesk;毛笔体做装饰 + 思源宋体做正文。
2. 配色:禁紫渐变白底;宣纸米为底、墨色文字、朱砂红为唯一强调色,CSS 变量管理。
3. 布局:禁止居中 hero / 三栏卡片 / 千篇一律圆角阴影盒;不对称编辑式 + 大留白;原句竖排。
4. 背景:不要纯色;宣纸渐变 + 墨晕模糊圆 + SVG 颗粒噪点。
5. 动效:全部集中到"抽卡揭晓":墨点绽放 → 逐行错峰浮现 → 朱砂印章回弹盖下 → SSR 光扫。
【交付】先给设计系统(色板+字体+一张卡)再铺全页。
```

---

## iOS / SwiftUI (iOS 17+)

**AI default look to forbid:**
- Type: SF Pro as the main/display face (the #1 native "AI default look").
- Color: system blue, default `.tint`, untouched accent.
- Structure: `List` / `Form` / default `NavigationStack` styling (looks like a Settings screen).
- Iconography: stock SF Symbols used as primary visuals.
- Material abuse: `.ultraThinMaterial` / default rounded card + `.shadow()` on everything.

**Native superpowers (put in the high-impact moment):**
- **Haptics:** `CoreHaptics` or `UIImpactFeedbackGenerator` / `.sensoryFeedback` — e.g. a "stamp
  press" thump at the reveal. Web cannot do this.
- **Speech:** `AVSpeechSynthesizer` for native TTS readout.
- **Share:** `ShareLink` + `ImageRenderer` to render a view to an image and share.
- **Particles/atmosphere:** `Canvas` + `TimelineView` (or SpriteKit emitter) at ProMotion 120Hz.
- **Continuity:** `matchedGeometryEffect` to morph a tapped item into the detail card;
  `withAnimation(.spring)` for staggered entrance.

**Good-citizen constraints (required):** bundle custom fonts (`UIAppFonts` in Info.plist +
`Font.custom`), Dynamic Type scaling, dark mode via Asset Catalog semantic colors, safe-area
insets (notch / Dynamic Island / home indicator), 44pt min touch target, VoiceOver labels.

**Vertical Chinese text caveat:** SwiftUI has no `writing-mode: vertical-rl`. Implement with a
per-character `VStack`, or rotate a `Text`, or use an `AttributedString` workaround.

**Filled example:**
```
用 SwiftUI(iOS 17+)做「抽卡揭晓」界面。写代码前先定美学方向并简述设计意图。
【美学方向】水墨留白 + 杂志竖排 + 一处极致的揭晓时刻。
【硬约束——避开 iOS 默认味】
1. 字体:禁用 SF Pro 作主视觉;bundle 毛笔体+思源宋体,Info.plist 注册,Font.custom 调用,走 Dynamic Type。
2. 配色:禁 system blue / 默认 tint;宣纸米底 + 墨色 + 朱砂红强调;Asset Catalog 语义色 + 深色(墨夜)主题。
3. 控件:禁 List/Form/默认 NavigationStack;不要默认圆角卡+.shadow+.ultraThinMaterial;自绘卡片;原句竖排(逐字 VStack)。
4. 背景:不要纯色 Color;宣纸渐变 + 墨晕模糊圆 + 颗粒噪点。
5. 动效集中在"揭晓":CoreHaptics 印章震动 → 竖排原句 .spring 错峰浮现 → 朱砂印章 scale+rotation 回弹 → SSR 金边光扫;matchedGeometryEffect 让签连贯放大成卡。
6. 原生能力:AVSpeechSynthesizer 朗读;ShareLink + ImageRenderer 渲染卡片成图分享。
【交付】先给 Color/Font 扩展 + 一个 QuoteCard 组件 + 可预览 Preview,确认后再铺全页。
```

---

## Android / Jetpack Compose

**AI default look to forbid:**
- Default Material 3 baseline theme straight out of the template.
- Roboto as the main face; default dynamic-color purple seed.
- Stock Material components (`Card`, `Button`, `TopAppBar`) with no restyling.

**Native superpowers:** `HapticFeedback`; `animate*AsState` / `AnimatedContent` / `updateTransition`
for the orchestrated reveal; `Canvas` (DrawScope) for particles and texture; predictive-back;
`SharedTransitionLayout` for continuity.

**Good-citizen constraints:** custom fonts via `FontFamily`; support dynamic color *as an option*
but override seed for brand identity; dark theme via `MaterialTheme` color schemes; 48dp min touch
target; TalkBack content descriptions; edge-to-edge with insets.

**Filled example skeleton:** same structure as iOS — swap section 1 to "禁用 Roboto/默认 M3 baseline,
用自定义 FontFamily", section 3 to "禁用未改样式的 Material 组件,自绘卡片", section 6 to
"HapticFeedback + Canvas 粒子 + SharedTransitionLayout".

---

## Flutter

**AI default look to forbid:** default `MaterialApp`/`CupertinoApp` widgets unstyled; Roboto;
`ThemeData()` defaults; stock `Card`/`AppBar`.

**Native superpowers:** `CustomPainter` for bespoke visuals and particles; implicit
(`AnimatedFoo`) + explicit (`AnimationController`) animations; `Hero` transitions; `HapticFeedback`;
`ShaderMask` / `BackdropFilter` for atmosphere.

**Good-citizen constraints:** bundle fonts in `pubspec.yaml`; `MediaQuery` text scaling; dark theme;
`Semantics` for accessibility; `SafeArea`.

---

## Quick adaptation checklist

When moving a design to a new platform, copy and fill:

```
- [ ] Aesthetic direction: kept identical from prior platform
- [ ] Negative list: swapped to THIS platform's "AI default look"
- [ ] Native capabilities: chosen for the ONE high-impact moment
- [ ] Good-citizen constraints: safe area, touch target, dynamic type, dark mode, a11y
- [ ] Workflow: design system + one signature component first, then confirm, then full build
```
