# 3D Card Wall

基于 Three.js 的 3D 卡片交互墙，纯静态 HTML/CSS/JS，零框架依赖。

A 3D interactive card wall built with Three.js. Pure static HTML/CSS/JS, zero framework dependencies.

## 快速开始 / Quick Start

启动任意本地 HTTP 服务器 / Start any local HTTP server:

```bash
python -m http.server 8080
# or
npx serve .
```

浏览器打开 `http://localhost:8080` / Open `http://localhost:8080` in your browser.

> 必须通过 HTTP 服务器访问，`file://` 协议下 XHR 无法加载 Three.js CDN。
> Must be served via HTTP — `file://` protocol cannot load Three.js via XHR.

## 交互功能 / Interactions

| 操作 / Action | 效果 / Effect |
|------|------|
| **鼠标拖拽** / Drag (hold) | 旋转圆柱卡片墙，松手后有惯性滑动 / Rotate the cylinder wall with inertia |
| **鼠标悬停** / Hover | 卡片向前浮出 + 金色发光边框 + tooltip / Card pops out with golden glow + tooltip |
| **点击卡片** / Click | 卡片短暂高亮闪烁 / Card flashes briefly |
| **触屏拖拽** / Touch drag | 移动端同样支持 / Mobile touch support |
| **自动旋转** / Auto-rotate | 无操作时缓慢自转 / Slow auto-rotation when idle (`presetSpeed = 0.0018`) |

## 项目结构 / Structure

```
photo-wall-3d/
├── index.html    # 所有内容 HTML + CSS + JS / All content
└── README.md
```

## 自定义 / Customization

### 修改卡片数量 / Card Count

编辑 `ROWS`（行）和 `COLS`（列），默认 20×24 = 480 张。
Edit `ROWS` and `COLS`, default 20×24 = 480 cards.

### 修改卡片颜色 / Colors

编辑 `CARD_COLORS` 数组。
Edit the `CARD_COLORS` array.

### 修改卡片内容 / Content

编辑 `CARDS` 数组中的 `title` 和 `color`。也可在 `initDesktop` 中修改 Canvas 纹理绘制逻辑。
Edit the `title` and `color` fields in the `CARDS` array, or modify the Canvas texture logic in `initDesktop`.

### 修改圆柱大小 / Cylinder Size

调整 `CYL_R`（半径 / radius，默认 210）、`CARD_W`、`CARD_H` 等参数。

### 修改旋转速度 / Rotation Speed

`presetSpeed` 控制自动旋转速度，设为 `0` 停止自动旋转。
Set `presetSpeed` to `0` to disable auto-rotation.

## 集成 / Integration

`index.html` 是自包含的单文件 / Self-contained single file:

- 直接用 `<iframe>` 嵌入任何页面 / Embed via `<iframe>`
- 提取 `<script>` 中的 Three.js 逻辑集成到 React/Vue/Astro 等框架 / Extract Three.js logic into any framework
- Three.js 从 CDN 加载，无需 npm 安装 / Three.js loaded from CDN, no npm install

## 技术栈 / Tech Stack

- **Three.js 0.157** — CDN 加载，零安装 / CDN, zero install
- **Canvas API** — 动态生成卡片纹理 / Dynamic card texture generation
- **原生 JS / Vanilla JS** — 无框架依赖 / No framework
