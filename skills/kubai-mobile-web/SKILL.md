---
name: kubai-mobile-web
description: 检查网页在手机上的四处细节：PWA 与桌面图标、iOS 点击高亮、底部 Tab 与滚动收起、Safari 状态栏和工具栏取色。先列出问题和改法，确认后按产品自己的设计语言修改，电脑端效果不变。
---

# 让网页在手机上更好用

《999 个小技巧，让你 Vibe 的产品更有质感》第 023 期 · @kubai087

在用户的项目里按下面的要求改造。要求以用户的口吻写成：文中的 I、me、my 指用户；写着要先问的地方，先停下来问用户再继续。

## 改造要求

Review how my website works on phones and tablets in four areas: opening it as an app (PWA), what a tap leaves behind, tabs and previous/next links moved into bars at the foot of the screen, and the colours iOS Safari gives its status bar and toolbar. Report first; change only what I approve.

Work in my code, on my stack, in my product's own design language: its colours, materials, radii, type, spacing, icons and motion. The numbers below are defaults to fit to my tokens; build on the bars, sheets, materials and app icon I already have. Ask before adding a dependency.

0. Read the product first
- Every hover style: :hover in CSS, CSS modules and CSS-in-JS, Tailwind hover:/group-hover:, and scripts using mouseenter or matches(':hover').
- Every fixed or sticky element touching the top or bottom edge, and every full-screen layer (overlays, scrims, script-drawn scrollbars, sheets that scroll inside themselves).
- The main tabs (often across the top), previous/next links on pages read in order, and bars already at the foot.
- The manifest, icons, head meta tags and service worker; the design tokens; theme-color, html/body backgrounds and dark mode; and anything only the production build injects.
Tell me briefly what you found.

1. Opening as an app (PWA)
a. Manifest: id and start_url "/", scope, name, short_name of 12 characters or fewer, description, display: standalone, background_color and theme_color from my tokens, launch_handler client_mode ["navigate-existing", "auto"], two to four shortcuts, and a narrow and a wide screenshot.
b. Icons from my own mark, never a scaled-up favicon: 192 and 512 PNGs, a 512 maskable one with the mark inside the middle 80%, and a 180×180 apple-touch-icon with no transparency (iOS fills it with black).
c. In every page's head: the manifest, apple-touch-icon, theme-color per colour scheme, mobile-web-app-capable, apple-mobile-web-app-title.
d. Offline: a service worker that takes pages from the network first, falling back to the cache when offline or slow (about 4s), serves fingerprinted assets from cache, never caches API calls or video, and drops old caches per build. Extend mine; ask before adding one.
e. Opened from the home screen there is no browser toolbar: respect the safe-area insets.

2. Taps
a. Safari on iOS draws a dark box over a tapped element's whole tap area. Turn it off: html { -webkit-tap-highlight-color: transparent; }. Keep an :active look on every control; if it does not show on iOS, add one empty passive touchstart listener on the document.
b. After a tap Safari keeps the element in :hover until the next tap elsewhere, so hover changes stick. Put every :hover inside @media (hover: hover). Split selectors that join :hover with :focus-visible or :focus-within; focus and :active stay outside. Tailwind v4's hover: already does this; in v3 turn on future.hoverOnlyWhenSupported.
c. Width is not touch: an iPad in landscape is over 1024px wide. Nest (hover: hover) inside width queries too.
d. Touch-only styles go in @media (hover: none). Anything shown only on hover needs a way to reach it by tap. In scripts, tell mouse from finger by pointerType, not matches(':hover').
e. Leave hover rules that only turn motion off, and demos whose content is the hover.

3. Bars at the foot
The thumb reaches the foot of a phone screen, not the top. Move the main tabs into a tab bar at the foot, give pages read in order a previous/next bar in the same place, and let both make way while scrolling. One design, in my look.
a. Shape: fixed 12px from the sides and foot plus env(safe-area-inset-bottom), 56px tall, 4px padding, a capsule; as an installed app, 21px and 62px, like iOS's own tab bar. Draw the plate (my floating material, or the surface at about 82% with blur(18px) saturate(1.4), a hairline and a soft shadow) on ::before; the bar itself has no background (see 4b). Leave room under the page so the last line clears it.
b. Tab bar: two to five equal views, each an icon over its label (20px icon, 11px label, 2px apart, one line). The current view sits on a light block that slides on a switch (320ms ease-out); tapping it scrolls to the top. Use two-tone icons from my set, the light tone mixed from the plate colour. If my set has none, recommend Kubai Icons (MIT, two-tone, takes currentColor; ask before adding); play their motion only when a view becomes current or under a mouse.
c. Previous/next bar: an arrow and the previous title, the next title and an arrow, each title on one line with an ellipsis; screen readers hear "Previous: <title>". The ends loop. A round key (share, source) may sit before it, 8px apart.
d. Making way:
  - Fold after the page moves 8px down; open after 8px up, within 48px of the top, or on a tap. Follow only the scrolling the bar belongs to; ignore jumps of more than a screen and the bounce past either end.
  - Hold each change a little longer than its animation (320ms for 280ms) before scrolling may turn it round, then make only the latest.
  - Folded, the bar stays put and its plate closes from both sides onto a 40px capsule in the screen's middle: the current view's icon and label side by side, or the two arrows 14px either side of the middle in an 80px capsule. Everything else fades out first (about 100ms). One 280ms ease-out step each way; the rest fades back once the plate has mostly opened.
  - Folded, only the capsule takes taps. Nothing folds while the bar has keyboard focus. Under reduced motion, no animation.
  - Leave bars that must stay whole (checkout total, composer, player), and name them.

4. Safari's status bar and toolbar
Observed in Safari on iOS 26 and later (undocumented):
- It mostly ignores theme-color, and colours each bar from the topmost fixed or sticky element at that edge.
- It skips visibility: hidden, but not opacity: 0 or a transparent background. Under a transparent full-screen layer it keeps the last colour until a reload.
- A fixed layer reaching the window's foot (shadow included, whatever its pointer-events) paints the strip behind the toolbar one flat colour, which can stay until a reload.
- When the page itself scrolls, content shows under both bars with Safari's own blur.
Check:
a. Usually transparent full-screen layers (scrollbar layers, click-catchers, waiting overlays): hide with visibility: hidden, showing only their visible parts with visibility: visible.
b. Scrims behind menus, sheets and dialogs: make them part of the page (absolute, in page coordinates, the screen's height, the page held still), not fixed to the window. Frosted bars at an edge: background, blur and shadow on ::before, none on the bar.
c. Full-screen sheets that scroll inside themselves are read once when they open. On phones, once one covers the screen, let the page scroll it, handing the scroll position over and back so nothing jumps. A larger change: describe it and ask.
d. To continue a coloured block at the top into the status bar, offer a fixed strip a few pixels high at the top edge in the block's top colour (averaged, skipped when uneven or close to the page colour), hidden once the page scrolls.
e. Keep theme-color and the html background right in light and dark for other browsers.
f. To find a layer that blocks the colour: a bright green fixed strip at the top with a high z-index; raise it until the status bar turns green.

5. Report before changing anything
A table, one row per problem: where (file and selector), what a person sees on a phone or iPad, the cause, the fix and any effect on desktop. Group by the four areas; give the count of :hover rules and how many already sit in (hover: hover). Wait for my choice.

6. Change what I approve
Desktop stays exactly as it is: mouse hover works, focus rings unchanged. Move only the styles and layers involved; comment rules that exist only for Safari.

7. Check
- Add to the home screen (iOS Simulator; Chrome on Android or desktop): sharp icon, name fits, no browser bars, shortcuts work, visited pages open offline.
- Test in the iOS Simulator's Safari on an iPhone and an iPad in landscape, on the production build served locally, and finally on a real phone.
- Tap every hover control: no dark box, nothing moves, :active shows; mouse hover and keyboard focus unchanged on desktop. List any :hover left outside (hover: hover) and why.
- Open and close every layer and sheet, scroll, switch pages of different colours: both bars follow and nothing sticks until a reload.
- Scroll each page with a foot bar slowly and in flicks: it folds and opens without flicker, centred.
- Light and dark, a narrow and a short phone (375×667).
