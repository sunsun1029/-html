# 项目说明

## 项目概览

这是一个基于 Vue 3 和 Vite 的单页个人主页项目。页面内容围绕“孙婉晴”的个人作品集展开，包含首屏介绍、关于、近期作品、经历与能力、联系方式等区块。整体视觉是温暖浅色背景、深色文字、青绿色主色和珊瑚色强调色的作品集风格。

## 技术栈

- 前端框架：Vue 3，使用 `<script setup>` 单文件组件写法。
- 构建工具：Vite 6。
- 语言与模块：原生 JavaScript，项目启用 ESM，`package.json` 中设置了 `"type": "module"`。
- 样式：全局 CSS，集中在 `src/styles.css`。
- 字体：页面通过 Google Fonts 加载 `Noto Serif SC` 和 `Inter`。

## 目录结构

- `index.html`：Vite 入口 HTML，挂载 `#app`，设置页面标题、描述和字体预连接。
- `src/main.js`：创建 Vue 应用，挂载 `App.vue`，并引入全局样式。
- `src/App.vue`：主页面组件，包含页面内容数据、滚动状态、移动端菜单状态和完整模板。
- `src/styles.css`：全局样式、响应式布局、颜色变量、按钮、卡片、导航、首屏和各页面区块样式。
- `assets/hero-workspace.svg`：当前首屏使用的工作空间背景图。
- `assets/hero-workspace.png`：项目中保留的同主题位图资源，目前源码没有直接引用。
- `dist/`：Vite 构建产物目录，已在 `.gitignore` 中忽略。
- `share.html`：一个可直接分享的独立 HTML 文件，内联了构建后的 CSS 和 JavaScript；当前是未跟踪文件。

## 常用命令

```bash
npm run dev
npm run build
npm run preview
```

- `npm run dev`：启动本地开发服务器，脚本指定监听 `127.0.0.1`。
- `npm run build`：生成生产构建，输出到 `dist/`。
- `npm run preview`：预览生产构建，同样监听 `127.0.0.1`。

## 页面内容与行为

- 顶部导航固定在页面顶部，滚动超过 24px 后切换为浅色半透明背景。
- 移动端会显示圆形菜单按钮，点击后展开纵向导航菜单。
- 导航锚点包括 `#about`、`#work`、`#experience`、`#contact`。
- 作品列表由 `src/App.vue` 中的 `works` 数组驱动，目前有 3 个作品卡片。
- 技能标签由 `src/App.vue` 中的 `skills` 数组驱动。
- 联系方式目前使用占位邮箱 `hello@example.com`，外链指向 GitHub 和 LinkedIn 首页。

## 样式约定

- 颜色变量定义在 `src/styles.css` 的 `:root` 中，主要包括 `--bg`、`--surface`、`--ink`、`--muted`、`--teal`、`--coral` 等。
- 页面整体使用全局样式，没有 CSS Modules 或 scoped style。
- 主要布局使用 CSS Grid 和 Flexbox。
- 响应式断点主要是 `860px` 和 `560px`。
- 卡片圆角为 `8px`，按钮使用胶囊形圆角。
- 文本设置了 `overflow-wrap: anywhere`，用于降低中文或长字符串溢出的风险。

## 开发注意事项

- 源文件包含中文内容，读取或编辑时应保持 UTF-8 编码，避免 PowerShell 默认编码导致的乱码误判。
- 不要直接修改 `dist/` 中的构建产物；应修改 `src/`、`assets/` 或 `index.html` 后重新构建。
- 如需改个人信息、作品、技能、导航文案，优先修改 `src/App.vue` 中的数据和模板。
- 如需调整视觉风格，优先从 `src/styles.css` 的 CSS 变量和对应区块样式入手。
- 如果更新首屏图像，当前源码引用的是 `assets/hero-workspace.svg`；替换资源时同步检查 `src/App.vue` 的 import。
- `share.html` 是独立分享文件，不属于标准 Vite 构建入口；若要维护它，应先确认它是否需要继续作为手工生成或发布用文件保留。

## 当前仓库状态观察

- `.gitignore` 忽略了 `node_modules/` 和 `dist/`。
- 当前项目已安装依赖，存在 `node_modules/` 和 `package-lock.json`。
- 当前工作区里 `share.html` 是未跟踪文件。
