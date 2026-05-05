# 个人学术主页维护指南

## 项目概览

**网站地址**：https://mingcheng-zhang.github.io  
**GitHub 仓库**：https://github.com/Mingcheng-Zhang/mingcheng-zhang.github.io  
**模板来源**：[Luka Homepage Template](https://github.com/wzsyyh/luka-homepage-template)（纯静态 HTML/CSS/JS，无构建工具）  
**本地路径**：`C:\Personal_Website`  
**Codex 维护说明**：见 `AGENTS.md`

---

## 网站所有者

- **姓名**：Mingcheng Zhang
- **身份**：Macquarie University 应用金融系 PhD 一年级学生
- **研究方向**：Household Finance、Behavioral Finance
- **学术邮箱**：mingcheng.zhang@mq.edu.au
- **GitHub**：Mingcheng-Zhang
- **LinkedIn**：https://www.linkedin.com/in/mingcheng-zhang-2058b7390

---

## 文件结构

```
C:\Personal_Website/
├── index.html              # 主页（所有内容均在此文件）
├── assets/
│   ├── css/
│   │   ├── theme-luka.css  # 主题样式（配色、布局）
│   │   └── font_sans_serif.css
│   ├── img/
│   │   ├── avatar.svg      # 头像占位图（待替换为真实照片）
│   │   ├── favicon.svg
│   │   └── institution.svg
│   ├── js/
│   │   └── scale.fix.js
│   └── cv/
│       └── README.md       # CV PDF 待上传至此目录，命名 cv.pdf
├── CLAUDE.md
└── AGENTS.md               # Codex 项目维护指南
```

---

## 配色系统（绿色主题）

所有颜色通过 CSS 变量在 `theme-luka.css` 的 `:root` 和 `[data-theme]` 块中定义：

| 变量 | 亮色值 | 用途 |
|------|--------|------|
| `--luka-bg` | `#FAFAF7` | 页面背景 |
| `--luka-text` | `#252A24` | 主文字 |
| `--luka-accent` | `#3F6B57` | 标题/链接/边框/徽章 |
| `--luka-accent-dark` | `#2E4F40` | 强调用深绿 |
| `--luka-accent-light` | `#E8F0EB` | 摘要背景/图标背景 |
| `--luka-gold` | `#B89B5E` | 月亮图标/金色点缀 |
| `--luka-secondary` | `#6F766E` | 次级文字 |
| `--luka-border` | `#D8E0D8` | 边框 |

暗色模式变量在 `[data-theme="dark"]` 块中，主色为 `#6aab8c`（亮绿）。

---

## 页面结构（index.html）

### 侧边栏（sidebar）
- 头像图片：`assets/img/avatar.svg`（待替换）
- 姓名、邮箱
- 社交图标：Email、LinkedIn
- Visitor Map：MapMyVisitors 图片版，tracker ID `9oRezoFUGIwCng6OSVy_Z3OTeHI32arGLkjfkTKKmjQ`
  - 亮/暗色地图通过 JS 动态切换 `<img>` 的 `src`

### 主内容区（content）
- **About Me**：个人简介，无 CV 链接（待后续添加）
- **Working Papers**：论文卡片列表
- **Work in Progress**：占位，内容待补充

---

## 论文卡片格式

在 `#working-papers` 区块内添加如下结构：

```html
<div class="paper-card">
  <div class="paper-title">论文标题</div>
  <div class="paper-authors">With 合作者A, and 合作者B</div>
  <!-- 有状态时加徽章，否则省略 paper-meta -->
  <div class="paper-meta">
    <span class="status-badge">Revise &amp; Resubmit at 期刊全称</span>
  </div>
  <details class="paper-abstract">
    <summary>Abstract</summary>
    <div class="abstract-body">摘要内容</div>
  </details>
</div>
```

**约定**：
- 作者栏不写自己名字，格式为 `With X, and Y`
- 期刊名写全称，`&` 用 `&amp;` 转义
- 摘要默认折叠，纯 CSS 实现（`<details>`/`<summary>`）
- 无投稿状态时省略 `paper-meta` 整块

---

## 常用操作

### 推送更新到 GitHub

```bash
cd "C:\Personal_Website"
git add -A
git commit -m "描述修改内容"
git push
```

### 替换头像照片

将照片文件重命名或复制到 `assets/img/avatar.jpg`（或 `.png`），  
然后在 `index.html` 第 40 行将 `src` 改为对应路径：

```html
<img src="assets/img/avatar.jpg" alt="Mingcheng Zhang">
```

### 上传 CV

将 PDF 文件放到 `assets/cv/cv.pdf`，  
在 About Me 段落末尾加一行：

```html
<p><strong><a href="assets/cv/cv.pdf" target="_blank" rel="noopener">Download my CV</a></strong></p>
```

### 修改地图配色

地图颜色参数写在 `index.html` 的 JS 块 `loadMap` 函数中：
- `cl` = 大陆色，`co` = 海洋色，`cmo` = 历史访客，`cmn` = 近期访客

---

## 待办事项

- [ ] 上传真实头像照片（替换 `assets/img/avatar.svg`）
- [ ] 上传 CV PDF（`assets/cv/cv.pdf`）并在 About Me 添加下载链接
- [ ] Work in Progress 部分填入具体内容
- [ ] 添加 Google Scholar 主页链接（有账号后更新社交图标）
