---
title: Astro/Fuwari 个人博客搭建与部署
published: 2025-12-17
description: 记录如何从零开始搭建 Fuwari 博客，并使用 GitHub Actions 自动部署到 GitHub Pages。
tags: [Blog, GitHub Actions, Astro]
category: Tech
draft: false
---

## 1. 简介

本文记录了如何使用 [Fuwari](https://github.com/saicaca/fuwari) 主题搭建一个 Astro 博客，并通过 GitHub Actions 部署到 GitHub Pages。

文中所有示例都会使用占位符（例如 `<your-github-username>`、`<your-repo-name>`），不包含任何真实的用户名、仓库名或本机路径，你在自己环境里按需替换即可。

## 2. 环境准备

- Node.js（推荐 v18+）
- pnpm
- Git
- 一个 GitHub 账号（用于托管代码和开启 GitHub Pages）
- 任意现代浏览器

## 3. 初始化 Fuwari 博客

这里假设你希望把博客代码放在一个新的仓库中，并基于 Fuwari 模板开始。

### 3.1 通过模板创建 GitHub 仓库

1. 打开 Fuwari 仓库：<https://github.com/saicaca/fuwari>
2. 点击 **Use this template** -> **Create a new repository**。
3. 仓库名使用 `<your-repo-name>`（例如 `blog` 或 `my-blog`）。

### 3.2 克隆到本地

在本地选择一个你喜欢的目录，执行：

```bash
git clone git@github.com:<your-github-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 3.3 安装依赖与本地开发

在项目根目录执行：

```bash
pnpm install
pnpm dev
```

默认情况下，Astro 会在本地启动一个开发服务器（一般是 <http://localhost:4321>），你可以在浏览器中预览博客效果。

## 4. 配置 Astro 与 Fuwari

下面是几个常用的配置项，帮助你把博客变成「自己的」：

### 4.1 站点信息（`astro.config.mjs`）

在 `astro.config.mjs` 中，配置成类似这样（以项目站点为例）：

```js
import { defineConfig } from "astro/config";

export default defineConfig({
  site: "https://<your-github-username>.github.io",
  base: "/<your-repo-name>",
});
```

如果你的仓库名就是 `<your-github-username>.github.io`，那它属于用户主页站点，可以省略 `base`：

```js
export default defineConfig({
  site: "https://<your-github-username>.github.io",
});
```

### 4.2 个人信息与头像（`src/config.ts`）

Fuwari 提供了一个 `profileConfig` 用来配置头像、昵称、简介等。示例：

```ts
export const profileConfig = {
  avatar: "https://example.com/avatar.png", // 可以是绝对 URL，或本地 /assets 路径
  name: "Your Name",
  bio: "一句话简介",
  links: [
    {
      name: "GitHub",
      icon: "github",
      url: "https://github.com/<your-github-username>",
    },
    // ...
  ],
};
```

这里的链接、头像地址等都建议使用你自己的值，但在公开文档或截图里可以继续保留占位符，避免暴露隐私。

### 4.3 关于页面（`src/content/spec/about.md`）

你可以在关于页面里使用 HTML + Markdown 混合的方式展示头像和自我介绍，例如：

```md
<p>
  <img
    src="https://example.com/avatar.png"
    alt="你的头像"
    style="width: 100%; border-radius: 16px; object-fit: cover;"
  />
</p>

这里写一些自我介绍，可以使用 **Markdown** 语法。
```

## 5. 部署到 GitHub Pages

下面以 GitHub Pages + GitHub Actions 的方式为例说明部署流程。

### 5.1 创建 GitHub 仓库并推送代码

1. 在 GitHub 上新建一个仓库，名称为 `<your-repo-name>`。
2. 将本地代码与远程仓库关联并推送：

```bash
git init
git add .
git commit -m "Init blog with Fuwari"
git branch -M main
git remote add origin git@github.com:<your-github-username>/<your-repo-name>.git
git push -u origin main
```

### 5.2 配置 GitHub Pages

1. 打开仓库页面，进入 **Settings -> Pages**。
2. 在 **Build and deployment** 中选择 **GitHub Actions** 作为 Source。

### 5.3 GitHub Actions Workflow 示例

在仓库中新建文件 `.github/workflows/deploy.yml`，例如：

```yaml
name: Deploy Astro site to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Deploy with Astro
        uses: withastro/action@v3
        with:
          path: .
          node-version: 20
          package-manager: pnpm@9
```

如果你使用的分支不是 `main`，记得把上面的 `branches: [ main ]` 改成你实际的分支名。

## 6. 常见问题

1. **Git 代理 / 网络问题**：如果访问 GitHub 较慢，可以在 Git 中配置合适的代理，或使用镜像站点进行克隆，然后再修改远程地址为正式的 GitHub 仓库。
2. **SSH 多账号问题**：在同一台机器使用多个 GitHub 账号时，可以通过编辑 `~/.ssh/config` 来区分不同的私钥和 Host，避免推错仓库。
3. **GitHub Pages 404 / 样式错位**：大多与 `astro.config.mjs` 中的 `site`、`base` 配置不一致有关。确认线上访问地址与本地配置完全对应。

## 7. 总结

Fuwari 是一个外观漂亮且配置简单的 Astro 博客主题。结合 GitHub Actions 和 GitHub Pages，可以实现「推送即部署」的工作流。

在公开分享配置或文章时，记得使用占位符替代真实的用户名、仓库名和本机路径，以避免泄露个人隐私信息.
