# 3D Card Wall

基于 Three.js 的 3D 卡片交互墙，纯静态 HTML/CSS/JS，零框架依赖。

## 快速开始

启动任意本地 HTTP 服务器：

```bash
python -m http.server 8080
# 或
npx serve .
```

浏览器打开 `http://localhost:8080`。

> 必须通过 HTTP 服务器访问，`file://` 协议下 XHR 无法加载 Three.js CDN。

## 交互功能

| 操作 | 效果 |
|------|------|
| **鼠标拖拽**（按住拖动） | 旋转圆柱卡片墙，松手后有惯性滑动 |
| **鼠标悬停** | 卡片向前浮出 + 金色发光边框 + tooltip 显示卡片信息 |
| **点击卡片** | 卡片短暂高亮闪烁 |
| **触屏拖拽** | 移动端同样支持拖拽旋转 |
| **自动旋转** | 无操作时缓慢自转（`presetSpeed = 0.0018`，可在代码中调整） |

## 项目结构

```
films-3d/
├── index.html    # 所有内容（HTML + CSS + JS）
└── README.md
```

## 自定义

### 修改卡片数量

编辑 `ROWS`（行数）和 `COLS`（列数），默认 20×24 = 480 张卡片。

### 修改卡片颜色

编辑 `CARD_COLORS` 数组，支持任意 CSS 颜色值。

### 修改卡片内容

编辑 `CARDS` 数组中的 `title` 和 `color` 字段。也可以在 `initDesktop` 中修改 Canvas 纹理绘制逻辑。

### 修改圆柱大小

调整 `CYL_R`（半径，默认 210）、`CARD_W`、`CARD_H` 等参数。

### 修改旋转速度

`presetSpeed` 变量控制自动旋转速度，设为 `0` 则停止自动旋转。

## 集成到其他框架

`index.html` 是自包含的单文件，可以：
- 直接用 `<iframe>` 嵌入任何页面
- 提取 `<script>` 中的 Three.js 逻辑集成到 React/Vue/Astro 等框架
- Three.js 从 CDN 加载，无需 npm 安装

## 技术栈

- **Three.js 0.157** — CDN 加载，零安装
- **Canvas API** — 动态生成卡片纹理，无需外部图片
- **原生 JS** — 无框架依赖
