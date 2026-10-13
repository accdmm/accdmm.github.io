# 个人主页（site/）

单页个人主页。**纯手写 HTML / CSS / JS，零框架、零构建、零外部请求**，
一个 `index.html` 就是全部（含样式、脚本、Canvas 动效、内联 SVG 图标）。

## 本地预览

直接双击 `index.html` 即可，不需要起服务器。

## 部署到 GitHub Pages

### 方案 A（推荐）：用户主页仓库

1. 新建仓库，仓库名**必须**是 `accdmm.github.io`
2. 把本目录的 `index.html` 和 `.nojekyll` 放到仓库根目录
3. 等 1 分钟左右，访问 **https://accdmm.github.io**

好处：地址最短最好记，而且会自动成为 GitHub 账号的"网站"字段候选值。

### 方案 B：普通仓库开 Pages

1. 把文件推到任意仓库（例如 `homepage`）
2. 仓库 Settings → Pages → Source 选 `Deploy from a branch`，分支 `main`、目录 `/ (root)`，保存
3. 访问 `https://accdmm.github.io/<仓库名>/`

> 注意：方案 B 的地址带路径，如果页面里有绝对路径引用会失效。本页所有资源都是内联的，
> 所以两种方案都能直接用，不需要改任何代码。

## 上线后建议顺手做的两件事

1. 在 GitHub `Settings → Public profile → Website` 填上主页地址（主页右侧栏会显示）
2. 在仓库 Settings → Social preview 上传一张分享图（1280×640），链接被转发时更好看

## 为什么不用第三方炫酷组件

常见的 `shields.io`、`github-readme-stats`、`*.vercel.app` 这类徽章与统计卡**都是外网图片服务**，
国内网络下经常加载不出来，页面上会直接出现破图 —— 比不加更难看。

本页因此全部自建：字体用系统字体栈、动效用 Canvas 与 CSS、图标用内联 SVG。
**没有任何外部请求，在国内打开是瞬开，也不会因为第三方服务挂掉而破相。**

## 文件说明

| 文件 | 说明 |
|---|---|
| `index.html` | 页面本体（样式 + 结构 + 脚本全在一个文件里） |
| `.nojekyll` | 告诉 GitHub Pages 跳过 Jekyll 处理，部署更快 |
| `desktop.png` / `mobile.png` | 桌面端与移动端渲染截图（仅供预览，可以不部署） |
| `full.png` | 整页长截图（仅为预览） |

## 无障碍与降级

- 所有动效都遵循 `prefers-reduced-motion`，开启后自动降级为静态
- 内容默认可见，入场动画由 JS 添加类名触发；即使 JS 完全不可用，页面依然完整可读
- 进度条、粒子场等纯装饰元素标记了 `aria-hidden`
