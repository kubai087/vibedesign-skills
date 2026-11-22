# Feedback and states

## 009 Overlays (rule)

- Also called: 浮层组件的选择规则, 浮层, 弹窗, 抽屉
- Applies: Any product with tooltips, popovers, confirmations, drawers or dialogs.
- Signals: Tooltip, Popover, Popconfirm, Dialog, Modal, Drawer, Sheet, confirm(; a dialog for a one-item delete; a drawer used to confirm; a tooltip holding buttons; two components doing the same job.
- Skip: Products with almost no floating UI.
- Demo: https://vibedesign.tips/009-overlays/
- Text: tips/009-overlays.md (6.4k characters)

## 016 Toast or notification (rule)

- Also called: Toast 与通知的选择与改造, Toast, 通知
- Applies: Any product that tells people something happened.
- Signals: toast(, sonner, react-hot-toast, notistack, message.success, notification.open, Snackbar, alert(; a toast for an error on a form field; a toast for something another person did; no undo on a destructive action.
- Skip: None: nearly every product has messages.
- Demo: https://vibedesign.tips/016-toast-or-notification/
- Text: tips/016-toast-or-notification.md (11.8k characters)

## 017 Loading states (rule)

- Also called: 加载状态的诊断与改造, 加载状态, 骨架屏
- Applies: Any wait: page loads, lists, buttons that call the server, uploads, AI answers.
- Signals: isLoading or loading state; Spinner, Skeleton, Suspense fallback; useQuery, SWR, Apollo; a spinner centred on an empty page; a blocking overlay while saving; layout that jumps when data arrives.
- Skip: Static pages with no data loading.
- Demo: https://vibedesign.tips/017-loading-states/
- Text: tips/017-loading-states.md (12.2k characters)

## 022 Empty states (rule)

- Also called: 空状态的诊断与改造, 空状态, 空白页, 缺省页
- Applies: Lists, tables, boards and calendars, inboxes and notifications, search and filter results, dashboards and chart cards, folders, comments and members, first-run screens, pages that can fail to load and pages a person may not be allowed to open.
- Signals: Empty-state components (EmptyState, Empty, NoResults, ZeroState); a bare "No data" or "Nothing here"; generic illustrations, stock SVGs or emoji above an empty list; lists that render nothing at all; a spinner left in place after a failed load; a no-results screen that clears the search; a whole page replaced by an error when one card failed.
- Skip: Products where nothing is ever empty, and places that simply close or hide when empty (a notification tray that closes).
- Demo: https://vibedesign.tips/022-empty-states/
- Text: tips/022-empty-states.md (13.6k characters)
