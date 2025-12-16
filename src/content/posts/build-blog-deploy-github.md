---
title: 使用 Fuwari 搭建个人博客并部署到 GitHub Pages
published: 2025-12-17
description: 记录如何从零开始搭建 Fuwari 博客，并使用 GitHub Actions 自动部署到 GitHub Pages。
tags: [Blog, GitHub Actions, Astro]
category: Tech
draft: false
---

## 1. 简介

本文记录了如何使用 [Fuwari](https://github.com/saicaca/fuwari) 主题搭建个人博客，并配置 GitHub Actions 实现自动化部署。

## 2. 环境准备

- Node.js (v18+)
- pnpm
- Git

## 3. 安装步骤

### 克隆仓库

```bash
git clone https://github.com/saicaca/fuwari.git my-blog
cd my-blog
```

### 安装依赖

```bash
pnpm install
```

### 本地预览

```bash
pnpm dev
```

## 4. 部署到 GitHub Pages

### 修改配置

编辑 `astro.config.mjs`：

```javascript
export default defineConfig({
  site: "https://your-username.github.io",
  base: "/your-repo-name",
  // ...
});
```

### 配置 GitHub Actions

创建 `.github/workflows/deploy.yml` 文件，使用 `withastro/action` 进行自动构建和部署。

### 推送代码

```bash
git add .
git commit -m "Initial commit"
git push -u origin main
```

在 GitHub 仓库的 Settings -> Pages 中，将 Source 设置为 GitHub Actions。

## 5. 遇到的坑

1. **Git 代理问题**：需要确保 Git 配置了正确的代理端口。
2. **SSH 权限问题**：如果需要在同一台机器使用多个 GitHub 账号，可以通过 SSH Config 进行区分配置。

## 6. 总结

Fuwari 是一个非常美观且配置简单的 Astro 博客主题。配合 GitHub Actions，可以轻松实现 Push 即部署的流程。
