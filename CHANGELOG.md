# Changelog

本仓库基于 [SiranHQ/obsidian-QuadTasks](https://github.com/SiranHQ/obsidian-QuadTasks) 1.0.1（MIT）修改。

## 1.1.0 — 2026-11-08

首个独立发布的增强版。

### 新增

- **已完成任务显示开关**：底部 `Completed (n)` / `Hide completed` 按钮，在「只看未完成」和「全部显示」之间切换。过滤只发生在渲染层，`this.tasks` 与写回文件的内容始终完整，不会丢数据。
- **长按操作面板**：触屏上长按任务卡 450ms 弹出底部面板，可一键移动到任意象限、切换完成状态、删除；当前象限标「当前」。手指移动超过 10px 判定为滑动，不触发。
- **右键面板**：桌面端右键任务卡打开同一个面板，不想拖拽时更顺手。
- **Inbox 默认收起**：初始化固定 `showBuffer: false`，底部按钮显示 `Inbox (n)` 并在有暂存任务时高亮。
- 空象限提示区分状态：无任务显示 `No tasks`，全做完显示 `All done`。

### 修复

- **手机端任务文字竖排**：Obsidian 对 `ul` / `li` / `p` 的默认规则优先级高于插件样式，任务卡文字列被压到约 1 个字宽。改为「块级文本 + 控件绝对定位」，并把尺寸约束以**内联 `!important`** 写到元素上，主题与默认样式都改不动。
- **卡片被象限裁掉右半边**：`ul` 上未抵消的 `padding-inline-start: 40px` 导致卡片整体右移，再被象限的 `overflow: hidden` 裁切。现在 `padding-inline-start/end`、`width`、`box-sizing`、`max-width` 全部显式约束。
- 触屏上删除按钮 `×` 原本依赖 `:hover` 才显示，等于手机上无法删除任务；现在触屏常显（半透明）。
- 触屏关闭原生 HTML5 `draggable`，避免与长按手势冲突；桌面拖拽保持不变。

### 变更

- 插件显示名改为 **QuadTasks Enhanced**，`id` 仍为 `quadtasks`，可直接覆盖安装。
- 动作面板样式与布局关键约束内联化，降低对 `styles.css` 的依赖。
