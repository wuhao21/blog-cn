# blog-cn

中文个人博客，部署在 [blog.hwu.one](https://blog.hwu.one)。

基于 [Astro](https://astro.build/) + [Retypeset](https://github.com/radishzzz/astro-theme-retypeset) 主题。

## 常用命令

```bash
pnpm install        # 安装依赖（需要 Node 22+，pnpm 10）
pnpm dev            # 本地预览 http://localhost:4321
pnpm build          # 构建到 dist/
pnpm new-post 标题   # 新建文章 src/content/posts/标题.md
```

推送到 `main` 分支后由 GitHub Actions 自动构建并部署到 GitHub Pages。

## 配置

站点配置集中在 `src/config.ts`（标题、颜色、字体、评论、SEO 等）。
文章在 `src/content/posts/`，关于页在 `src/content/about/about-zh.md`。
