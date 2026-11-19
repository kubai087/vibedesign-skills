---
name: kubai-continuous-corners
description: 统一界面中的嵌套圆角：按“内圆角 = 外圆角 − 间距”逐层重新计算，再用 CSS superellipse 改为连续曲率圆角，不支持的浏览器保留普通圆角。适用于带卡片和表单的界面（nested radius, squircle）。
---

# 递进式圆角与连续曲率圆角

《999 个小技巧，让你 Vibe 的产品更有质感》第 004 期 · @kubai087

在用户的项目里按下面的要求改造。要求以用户的口吻写成：文中的 I、me、my 指用户；写着要先问的地方，先停下来问用户再继续。

## 改造要求

Make the corner radii in this UI consistent, then switch them to continuous
corners. Work on the screen or components I name; ask me if I have not
named them. If the project has radius tokens, change those instead of
hard-coding values.

1. Inner radius = outer radius - padding (r = R - p)
- Go from the outside in: dialog or card -> panels, inputs, buttons ->
  chips and tags. A box p inside a container with radius R gets R - p,
  so both corners share one center. Example: dialog 32, padding 16 ->
  panels and buttons 16; a chip 8 inside a 16 panel -> 8.
- Boxes on the same level share one radius. Never go below 4.
- Pills and circles stay fully round.
- Keep every padding, gap and radius on a 4px grid.

2. Continuous corners
- Keep border-radius and add the curve as progressive enhancement:
    @supports (corner-shape: superellipse(1.25)) {
      :where(*) { corner-shape: superellipse(1.25); }
    }
  Set corner-shape: round on pills and circles.
- Chrome and Edge 139+ render it; Safari and Firefox skip the block and
  show the plain border-radius.

When done, list every radius you changed as "element: old -> new".
