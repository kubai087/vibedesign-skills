# Vibe Design Tips Skills

Agent Skills from [Vibe Design Tips](https://vibedesign.tips), Kubai's series "999 tips to make your vibe-coded product feel crafted". Each tip is a design rule or an effect with a live demo; the Skills let Claude Code, Codex, Cursor and other AI coding tools apply them to your product.

Version 2026.11.24. See [CHANGELOG.md](CHANGELOG.md) for what changed.

[中文说明](#中文)

## Install

Tell your AI coding tool:

```text
Install the kubai-design-tips Skill by following https://raw.githubusercontent.com/kubai087/vibedesign-skills/main/INSTALL.md
```

Or by hand, for Claude Code:

```sh
git clone --depth 1 https://github.com/kubai087/vibedesign-skills.git ~/.vibedesign-skills
ln -sfn ~/.vibedesign-skills/skills/kubai-design-tips ~/.claude/skills/kubai-design-tips
```

Without git, download [vibedesign-skills.zip](https://github.com/kubai087/vibedesign-skills/releases/latest/download/vibedesign-skills.zip) (also at [vibedesign.tips](https://vibedesign.tips/downloads/vibedesign-skills.zip)). [INSTALL.md](INSTALL.md) has every step.

## Use

Review a product, or name one tip by its number, English name or Chinese name. In Claude Code:

```text
/kubai-design-tips review the UI of this project
/kubai-design-tips 019
/kubai-design-tips add scroll cards to the landing page
```

In other tools, mention `kubai-design-tips` and the tip in your request.

## Update

Ask your AI coding tool to "update the design tips Skill", or run:

```sh
git -C ~/.vibedesign-skills pull --ff-only
```

## The Skills

`kubai-design-tips` holds every tip below: it reviews your product's UI, suggests what to change and applies the tips you choose. Each tip also has a Skill of its own.

| No. | Skill | Tip | 中文 | |
| --- | --- | --- | --- | --- |
| 001 | `kubai-skeuomorphic-buttons` | Skeuomorphic buttons | 有按压反馈的拟物按钮 | [Demo](https://vibedesign.tips/001-skeuomorphic-buttons/) |
| 002 | `kubai-cascade-menu` | Cascade menu | 级联菜单的安全区域与延时 | [Demo](https://vibedesign.tips/002-cascade-menu/) |
| 003 | `kubai-ascii-dither` | ASCII and dither | ASCII与像素抖色效果 | [Demo](https://vibedesign.tips/003-ascii-dither/) |
| 004 | `kubai-continuous-corners` | Continuous corners | 递进式圆角与连续曲率圆角 | [Demo](https://vibedesign.tips/004-continuous-corners/) |
| 005 | `kubai-drag-ripple` | Drag to reorder | 带避让动效的拖拽排序 | [Demo](https://vibedesign.tips/005-drag-ripple/) |
| 006 | `kubai-book-cards` | Book cards | 悬停时像书一样翻开的卡片 | [Demo](https://vibedesign.tips/006-book-cards/) |
| 007 | `kubai-type-switches` | Type switches | 中英文排版的CSS设置 | [Demo](https://vibedesign.tips/007-type-switches/) |
| 008 | `kubai-wiki-layout` | Wiki layout | 兼顾PC和移动端的Wiki布局 | [Demo](https://vibedesign.tips/008-wiki-layout/) |
| 009 | `kubai-overlays` | Overlays | 浮层组件的选择规则 | [Demo](https://vibedesign.tips/009-overlays/) |
| 010 | `kubai-liquid-glass` | Liquid glass | 液态玻璃材质 | [Demo](https://vibedesign.tips/010-liquid-glass/) |
| 011 | `kubai-easing-curves` | Easing curves | 按场景选择缓动曲线 | [Demo](https://vibedesign.tips/011-easing-curves/) |
| 012 | `kubai-message-bubbles` | Message bubbles | 消息气泡的材质与动效 | [Demo](https://vibedesign.tips/012-message-bubbles/) |
| 013 | `kubai-shockwave-glow` | Shockwave glow | 冲击波光环效果 | [Demo](https://vibedesign.tips/013-shockwave-glow/) |
| 014 | `kubai-card-delete` | Card delete | 卡片删除的四种消失效果 | [Demo](https://vibedesign.tips/014-card-delete/) |
| 015 | `kubai-ui-continuity` | UI continuity | 界面连续性诊断与改造 | [Demo](https://vibedesign.tips/015-ui-continuity/) |
| 016 | `kubai-toast-or-notification` | Toast or notification | Toast 与通知的选择与改造 | [Demo](https://vibedesign.tips/016-toast-or-notification/) |
| 017 | `kubai-loading-states` | Loading states | 加载状态的诊断与改造 | [Demo](https://vibedesign.tips/017-loading-states/) |
| 018 | `kubai-holo-card` | Holo card | 会倾斜和翻转的镭射卡片 | [Demo](https://vibedesign.tips/018-holo-card/) |
| 019 | `kubai-scroll-cards` | Scroll cards | 滚动驱动的五种卡片交互 | [Demo](https://vibedesign.tips/019-scroll-cards/) |
| 020 | `kubai-choice-controls` | Choice controls | 选择控件的诊断与改造 | [Demo](https://vibedesign.tips/020-choice-controls/) |
| 021 | `kubai-ring-cards` | Ring cards | 景深环形卡片与流体渐变 | [Demo](https://vibedesign.tips/021-ring-cards/) |
| 022 | `kubai-empty-states` | Empty states | 空状态的诊断与改造 | [Demo](https://vibedesign.tips/022-empty-states/) |
| 023 | `kubai-mobile-web` | Mobile web pages | 让网页在手机上更好用 | [Demo](https://vibedesign.tips/023-mobile-web/) |

## 中文

[Vibe Design Tips](https://vibedesign.tips)（《999 个小技巧，让你 Vibe 的产品更有质感》）的 Agent Skill。每个技巧是一条设计规则或一种效果，都有在线演示。装好后，Claude Code、Codex、Cursor 等 AI 编程工具可以按这些技巧检查和改进你的产品。

**安装**：把下面这句发给你的 AI 编程工具：

```text
按 https://raw.githubusercontent.com/kubai087/vibedesign-skills/main/INSTALL.md 里的步骤安装 kubai-design-tips 这个 Skill。如果打不开 GitHub，改用 https://vibedesign.tips/downloads/INSTALL.md
```

**使用**：检查整个产品，或按期号、英文名、中文名指定某一期。在 Claude Code 里输入 `/kubai-design-tips 检查这个项目的界面`、`/kubai-design-tips 019` 或 `/kubai-design-tips 给首页加滚动卡片`；在其他工具里，在需求中写明 `kubai-design-tips` 和要用的那一期即可。

**更新**：对 AI 编程工具说"更新 design tips Skill"，或者运行 `git -C ~/.vibedesign-skills pull --ff-only`。

**包含哪些 Skill**：`kubai-design-tips` 包含上表中的全部技巧，可以检查你的产品界面、给出修改建议，并按你选定的技巧修改。每个技巧也有单独的 Skill。

每次更新的内容见 [CHANGELOG.md](CHANGELOG.md)。
