# Next.js + Tauri 2.0 模板

![构建状态](https://github.com/shuaihaoV/tauri-template/workflows/release/badge.svg)
![CI状态](https://github.com/shuaihaoV/tauri-template/workflows/ci/badge.svg)
![License](https://img.shields.io/github/license/shuaihaoV/tauri-template)
![Release](https://img.shields.io/github/v/release/shuaihaoV/tauri-template)

这是一个使用 Next.js 和 Tauri 2.0 构建跨平台桌面应用的入门模板。

它集成了最新的前端技术栈，让您能够快速启动并构建现代化、高性能的桌面应用程序。

## ✨ 特性

- **[Next.js](https://nextjs.org/)**: 使用 App Router 和 Turbopack，提供极致的开发体验和性能。
- **[Tauri 2.0](https://tauri.app/)**: 使用 Rust 构建轻量、安全、跨平台的桌面应用后端。
- **[shadcn/ui](https://ui.shadcn.com/)**: 精美、可定制的 UI 组件库。
- **[Tailwind CSS](https://tailwindcss.com/)**: 一个功能类优先的 CSS 框架。
- **主题切换**: 支持亮色/暗色模式切换。
- **代码规范**: 集成 ESLint，保证代码质量。

## 🚀 开始使用

### 1. 环境准备

在开始之前，请确保您的开发环境中已安装以下工具：

1.  **Node.js**: [https://nodejs.org/](https://nodejs.org/)
2.  **Rust**: [https://www.rust-lang.org/](https://www.rust-lang.org/)
3.  **Tauri 环境依赖**: 根据您的操作系统，按照 [Tauri 官方文档](https://tauri.app/v2/guides/getting-started/prerequisites) 完成配置。

### 2. 安装

克隆项目到本地：

```bash
git clone <your-repo-url>
cd <project-folder>
```

包管理器安装依赖：

```bash
bun install
```

### 3. 开发

此项目包含两种开发模式：

- **Web 开发模式**: 仅启动 Next.js 前端应用。这对于快速调试 UI 非常有用。

  ```bash
  bun run dev
  ```

  在浏览器中打开 [http://localhost:3000](http://localhost:3000) 查看。

- **桌面应用开发模式**: 同时启动 Next.js 前端和 Tauri 后端。

  ```bash
  cargo tauri dev
  ```

  这将启动一个桌面窗口，并加载您的应用。

### 4. 构建

要构建生产环境的桌面应用，请运行：

```bash
cargo tauri build
```

构建完成后，安装包会出现在 `src-tauri/gen/release/bundle` 目录下。

## 📁 目录结构

- `app/`: Next.js 的页面、路由和布局。
- `components/`: 可复用的 React 组件，特别是 `shadcn/ui` 组件。
- `lib/`: 辅助函数和工具。
- `public/`: 静态资源文件。
- `src-tauri/`: 所有 Tauri 相关的 Rust 代码，包括后端逻辑和应用配置。

## 📚 了解更多

- [Next.js 文档](https://nextjs.org/docs)
- [Tauri 文档](https://tauri.app/v2/guides/)
- [shadcn/ui 文档](https://ui.shadcn.com/docs)
- [Tailwind CSS 文档](https://tailwindcss.com/docs)
