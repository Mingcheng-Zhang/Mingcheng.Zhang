# Codex 项目维护指南

## 项目概览

- 网站地址：https://mingcheng-zhang.github.io
- GitHub 仓库：https://github.com/Mingcheng-Zhang/mingcheng-zhang.github.io
- 本地路径：`C:\Personal_Website`
- 技术栈：纯静态 HTML/CSS/JavaScript，无 `package.json`，无构建工具
- 模板来源：[Luka Homepage Template](https://github.com/wzsyyh/luka-homepage-template)

这个仓库是 Mingcheng Zhang 的个人学术主页。大多数内容更新只需要修改 `index.html`；视觉样式集中在 `assets/css/theme-luka.css`。

## 重要文件

- `index.html`：主页结构和所有主要内容，包括 About Me、Working Papers、Work in Progress、访客地图和深浅色切换脚本。
- `assets/css/theme-luka.css`：主题配色、布局、响应式样式、论文卡片样式。
- `assets/css/font_sans_serif.css`：字体相关样式。
- `assets/js/scale.fix.js`：iPhone viewport 缩放辅助脚本，通常不需要修改。
- `assets/img/avatar.svg`：当前头像占位图，后续可替换为真实照片。
- `assets/img/favicon.svg`：站点 favicon。
- `assets/img/institution.svg`：模板保留的机构图标资源，当前主页未重点使用。
- `assets/cv/`：放置 CV PDF 的目录，目标文件名建议为 `cv.pdf`。
- `CLAUDE.md`：旧电脑上 Claude Code 使用的维护手册，可作为历史说明参考。
- `README.md` / `README.zh-CN.md`：原 Luka 模板说明。

## 当前站点内容

网站所有者：

- 姓名：Mingcheng Zhang
- 中文名：张洺铖
- 身份：Macquarie University Department of Applied Finance 一年级 PhD student
- 研究方向：Household Finance、Behavioral Finance
- 邮箱：mingcheng.zhang@mq.edu.au
- LinkedIn：https://www.linkedin.com/in/mingcheng-zhang-2058b7390

主页结构：

- 左侧栏：头像、姓名、邮箱、Email/LinkedIn 图标、MapMyVisitors 访客地图。
- 主内容：About Me、Working Papers、Work in Progress。
- 页脚：版权信息。

访客地图：

- 使用 MapMyVisitors 图片版。
- Tracker ID：`9oRezoFUGIwCng6OSVy_Z3OTeHI32arGLkjfkTKKmjQ`
- 明暗色地图参数在 `index.html` 内联脚本的 `loadMap(isDark)` 函数中。

## 编辑约定

- 默认保持现有静态结构，不引入框架、打包器或依赖。
- 主要内容更新优先编辑 `index.html`。
- 样式更新优先使用 `assets/css/theme-luka.css` 中已有 CSS 变量和类名。
- 保持页面语言为英文，维护文档可使用中文。
- HTML 中外部链接应保留 `target="_blank"` 和 `rel="noopener"`，除非是邮箱或站内链接。
- 期刊名、论文状态等学术信息要按用户提供的原文准确填写。
- 修改论文作者时，遵循当前约定：作者栏不写 Mingcheng 自己，格式为 `With X, and Y`。
- 有投稿状态时使用 `paper-meta` + `status-badge`；无状态时省略整个 `paper-meta`。
- 摘要默认使用 `<details class="paper-abstract">` 折叠。
- 不要随意改动 MapMyVisitors tracker ID、GitHub Pages 仓库地址、邮箱和 LinkedIn，除非用户明确要求。

## 论文卡片模板

```html
<div class="paper-card">
  <div class="paper-title">Paper Title</div>
  <div class="paper-authors">With Coauthor A, and Coauthor B</div>
  <div class="paper-meta">
    <span class="status-badge">Revise &amp; Resubmit at Journal Full Name</span>
  </div>
  <details class="paper-abstract">
    <summary>Abstract</summary>
    <div class="abstract-body">
      Abstract text.
    </div>
  </details>
</div>
```

如果论文没有状态，删除 `paper-meta` 整块。

## 常见任务

### 本地预览

这是静态网站，通常可以直接在浏览器打开 `index.html`。如果需要本地服务，可在项目根目录运行：

```powershell
python -m http.server 8000
```

然后访问：

```text
http://localhost:8000
```

### 替换头像

1. 将真实照片放到 `assets/img/avatar.jpg` 或 `assets/img/avatar.png`。
2. 修改 `index.html` 中头像路径：

```html
<img src="assets/img/avatar.jpg" alt="Mingcheng Zhang">
```

### 添加 CV 链接

1. 将 PDF 放到 `assets/cv/cv.pdf`。
2. 在 About Me 段落末尾添加：

```html
<p><strong><a href="assets/cv/cv.pdf" target="_blank" rel="noopener">Download my CV</a></strong></p>
```

### 推送更新

```powershell
git status
git add -A
git commit -m "Describe the update"
git push
```

## 验证清单

修改后至少检查：

- `git status --short` 确认改动范围符合预期。
- 页面主要链接仍然有效：邮箱、LinkedIn、访客地图、CV 链接如果已添加。
- 明暗色切换按钮能工作。
- 论文摘要折叠/展开能工作。
- 移动端宽度下侧边栏与正文没有明显重叠。

## 待办事项

- 上传真实头像照片，替换 `assets/img/avatar.svg`。
- 上传 CV PDF 到 `assets/cv/cv.pdf`，并在 About Me 添加下载链接。
- 继续完善 Work in Progress 部分。
- 有 Google Scholar 账号后，添加 Scholar 链接或图标。

