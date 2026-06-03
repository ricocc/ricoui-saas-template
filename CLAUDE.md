# CLAUDE.md

本文件为 AI coding assistants 提供编辑本仓库时需要遵循的上下文和约定。

## Project

RicoFast 是一个 static-first SaaS 官网模板，基于 Astro、Tailwind CSS v4、MDX 和可复用组件系统构建。

当前项目已中文化：界面文案和文档以中文为主；`DESIGN.md`、`skills`、组件名、路由、工具名和技术名等英文标识保持英文。

它是前端模板，不是完整后端 SaaS 产品。项目包含营销页、MDX Blog/Changelog、演示价格、演示 Auth 页面、演示联系表单、SEO、暗黑模式和设计系统文档。

## Primary Docs

- `docs/PRD.md`：当前实现范围。
- `docs/PLAN.md`：项目概览。
- `docs/DESIGN.md`：设计 tokens 和 UI 规则。
- `docs/plan/`：页面级记录。
- `README.md`：中文主文档。
- `README-zh.md`：旧中文入口兼容文件。

## Current Stack

| Layer | Choice |
| --- | --- |
| Framework | Astro 6.4 |
| Styling | Tailwind CSS v4 with `@theme` tokens |
| Content | MDX, `@astrojs/mdx`, Astro Content Layer |
| Icons | `@lucide/astro` |
| Motion | AOS, CSS animation, `motion` dependency |
| SEO | `@astrojs/sitemap`, `@astrojs/rss`, custom meta components |
| Type checking | TypeScript, `astro check` |
| Lint/format | Biome |
| Images | Static assets, `sharp` |

开发服务器端口在 `astro.config.mjs` 中配置为 `5200`。

## Commands

```bash
pnpm install
pnpm dev
pnpm build
pnpm preview
pnpm check
pnpm astro
```

`pnpm build` 会运行 `astro check && astro build`。

## Repository Layout

```text
src/
  assets/js/main.js        Header、dark mode、mobile menu、AOS init
  collections/             menu、social、tech stack JSON
  components/
    cards/                 BlogCard, TechStackCard
    elements/              PageHeader, SectionHeader, SeparatorLine
    home/                  HeroSection
    sections/              Header, Footer, Pricing, FAQ, BlogSection
    ui/                    Button, Badge, Logo, BrowserFrame, PricingToggle
    widgets/               Toc, Pagination, ToTop, TrackGa, OptimizedImage
  config/site.js           站点信息、SEO、社交链接、邮箱
  content/
    post/                  Blog MDX
    changelog/             Changelog MDX
  layouts/                 Layout, PageLayout, PostLayout, Meta
  pages/                   Astro routes
  styles/                  global tokens, article styles, AOS overrides
  content.config.js        Content Layer schemas
public/
  assets/
  rico/
  favicon.png
  og.jpg
docs/
  PRD.md
  PLAN.md
  DESIGN.md
  plan/
```

## Routes

当前路由包括：

- `/`
- `/features`
- `/pricing`
- `/blog`
- `/blog/[slug]`
- `/blog/page/[page]`
- `/changelog`
- `/about`
- `/contact`
- `/elements`
- `/sign-in`
- `/sign-up`
- `/signin`
- `/signup`
- `/rss.xml`
- `/404`

`/sign-in` 和 `/sign-up` 是首选 Auth 模板路由；`/signin` 和 `/signup` 作为居中卡片版本保留。

## Design System

设计 tokens 在 `src/styles/global.css`，文档在 `docs/DESIGN.md`。

重要规则：

- 全站字体使用 `Source Han Sans SC`, `Noto Sans SC`, `思源黑体`。
- Primary color: `--color-primary` = `#2d6dc3`
- Accent color: `--color-accent` = `#fad13b`
- Light canvas: `--color-bg-primary` = `#fdfaf5`
- Dark canvas: `--color-bg-primary-dark` = `#0b1220`
- Main max width: `--max-screen` = `1200px`
- Inner max width: `--inner-screen` = `800px`
- 常规 section 使用 `.site-container`。
- 文章和窄内容使用 `.inner-container`。
- Dark mode 是 class-based，并存储在 `localStorage.dark_mode`。

新增 UI 时：

- 优先使用现有 tokens。
- 优先使用现有组件。
- 浅色和深色样式一起考虑。
- 动效保持克制，并尊重 `prefers-reduced-motion`。
- 图标优先使用 `@lucide/astro`。
- 简单 UI 行为不要引入新依赖。

## Astro And Content Rules

- 使用 `src/content.config.js` 中的 Astro Content Layer collections。
- Blog/Changelog 使用 `getCollection()`。
- 内容路由使用 `entry.id`。
- 渲染使用 `render(entry)`。
- 环境变量使用 `import.meta.env`。
- 客户端公开变量必须使用 `PUBLIC_` 前缀。
- `getStaticPaths()` params 应为字符串。

Blog posts: `src/content/post/<slug>/index.mdx`。

Changelog entries: `src/content/changelog/*.mdx`。

## Styling Conventions

- 优先使用 Tailwind utilities 和项目 tokens。
- 不要随手写 one-off hex，除非是在扩展 token 系统。
- 表单、导航、按钮和正文都使用默认 sans 字体，即思源黑体字体栈。
- 主要营销 section 常用 `py-16 md:py-24`。
- 保留现有虚线边框语言。
- 完成 UI 前检查移动端文本是否溢出。

## SEO And Analytics

相关文件：

- `src/config/site.js`
- `src/layouts/Meta.astro`
- `src/components/widgets/Meta.astro`
- `src/components/widgets/TrackGa.astro`
- `src/pages/rss.xml.js`
- `public/og.jpg`
- `public/robots.txt`

环境变量：

```env
PUBLIC_SITE_URL=https://your-domain.com
PUBLIC_GA4_ID=
PUBLIC_UMAMI_ID=
```

Analytics 可选，本地开发不应要求填写 analytics ID。

## Before Editing

1. 先读相关页面或组件。
2. 涉及范围时检查 `docs/PRD.md`。
3. 改视觉前检查 `docs/DESIGN.md`。
4. 改页面时可查看 `docs/plan/*.md`。
5. 保留与任务无关的用户改动。

## After Editing

代码或内容路由变化后，优先运行：

- `pnpm build`
- `pnpm check`

文档改动可用文本扫描确认。

## Do Not

- 不要重新引入英文主文案，除非是技术名、工具名或文件名。
- 不要把静态 Auth/Contact 页面写成真实后端能力。
- 不要添加未在代码中体现的公开能力声明。
- 不要添加真实密钥或私有凭据。
- 没有明确请求时，不要替换 Astro + Tailwind + MDX 技术栈。
