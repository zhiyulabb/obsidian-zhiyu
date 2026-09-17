# 纸予颜色结构

颜色入口是 `src/color-schemes/zhiyu.scss`，由 `src/theme.scss` 在上游样式后加载。

1. `body.theme-light` / `body.theme-dark` 的 `--zhiyu-palette-*` 保存原始色值。
2. 同一文件把色值映射到 Obsidian 标准变量：`--color-base-*`、`--background-*`、`--text-*`、`--interactive-*`，以及导航、表格、复选框等组件变量。
3. `src/features/zhiyu-screenshot-overrides.scss` 只保存布局修正和组件适配，颜色引用标准变量。

通用悬停、普通按钮、导航和表格悬停统一引用 `--background-modifier-hover`；主按钮和选中状态引用 `--interactive-accent`；链接文字使用对比更强的 `--text-accent`。错误、警告、成功分别引用红、橙、绿语义色，深色模式有独立的亮度。

插件只要引用 Obsidian 标准变量，就能继承这套颜色。插件自己的固定色值、局部变量覆盖、iframe，以及用户 CSS 片段仍可能形成例外。不能仅凭构建成功就声称所有插件页面已完成实测。

验证过浅色/深色及默认、macOS、Cupertino、移动端 Cupertino、Fluent、Material、Tactile、Adwaita 共 16 种组合的核心 hover/accent 计算值，并加载已安装的纸予工作台 CSS 验证插件根容器继承。
