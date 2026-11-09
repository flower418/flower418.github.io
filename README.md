# Sunflower's Log

博客地址：https://flower418.github.io

用 [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 搭建，push 到 `main` 后由 GitHub Actions 自动构建发布，大约 1 分钟生效。

## 写一篇新文章

在 `content/posts/` 下新建一个 `.md` 文件，文件名就是网址，例如 `content/posts/ddpm-notes.md` 对应 `https://flower418.github.io/posts/ddpm-notes/`。文件开头写：

```yaml
---
title: "DDPM 学习笔记"
date: 2026-11-10T20:00:00+08:00
draft: false
tags: [diffusion]
summary: "首页列表里显示的一句话简介。"
---
```

然后正文用 Markdown 写，写完：

```bash
git add . && git commit -m "new post" && git push
```

注意：

- `draft: true` 的文章不会发布，适合写一半先存着。
- `date` 不能写成未来时间，否则这篇文章不会显示。
- 可以在 GitHub 网页上直接新建或编辑文件，提交后同样会自动发布。

## 公式

用 MathJax，写法和 LaTeX 一样：

- 行内：`$E = mc^2$`
- 独立一行：

  ```
  $$
  \mathcal{L} = \mathbb{E}_{t, x_0, \epsilon}\left[\|\epsilon - \epsilon_\theta(x_t, t)\|^2\right]
  $$
  ```

正文里如果要写真正的美元符号，写成 `\$`。

## 图片

最省事的做法是把文章写成文件夹：

```
content/posts/ddpm-notes/
├── index.md      # 文章正文
└── loss.png
```

正文里写 `![loss curve](loss.png)` 即可。

## 单篇文章的开关

在文章开头加这些可以覆盖全局设置：

```yaml
ShowToc: false      # 不显示目录
TocOpen: true       # 目录默认展开
hideMeta: true      # 不显示日期和阅读时间
```

## 常改的地方

都在 `hugo.yaml`：

- 博客名：`title` 和 `params.title`
- 首页欢迎语：`params.homeInfoParams`
- 社交链接：`params.socialIcons`，支持 `github`、`x`、`email`、`googlescholar`、`zhihu`、`rss` 等
- 界面语言：把 `languageCode` 改成 `zh-cn`，按钮和日期会变成中文
- 菜单：`menu.main`

关于页面在 `content/about.md`。

## 本地预览（可选）

```bash
brew install hugo
git submodule update --init
hugo server   # 打开 http://localhost:1313
```

## 结构

```
hugo.yaml                        站点配置
content/posts/                   文章
content/about.md                 关于页
layouts/_partials/extend_head.html   MathJax
static/                          favicon 等静态文件
themes/PaperMod/                 主题（git submodule）
.github/workflows/hugo.yaml      自动构建发布
```
