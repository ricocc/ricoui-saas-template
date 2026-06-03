# RicoFast PRD

> 本 PRD 描述当前已实现的 RicoFast 项目范围。当前项目已调整为中文项目，界面和文档以中文为主，技术名、文件名和工具名保持英文。

## 产品摘要

RicoFast 是一个 design-led SaaS 官网模板，基于 Astro、Tailwind CSS v4、MDX 和可复用组件系统构建。它帮助独立开发者、AI 工具团队、开发者平台团队和开源维护者更快发布一个有设计完成度的产品站。

项目是 static-first 前端模板，不是完整后端 SaaS 产品。它包含演示价格、演示 Auth 页面、演示联系表单、MDX 内容、SEO 基础、暗黑模式和设计系统文档。

## 定位

| 字段 | 当前值 |
| --- | --- |
| Product name | RicoFast |
| Category | Astro SaaS website template |
| Tagline | 面向 Astro 的高质感 SaaS 模板 |
| Core promise | 几天内上线一个像样的 SaaS 官网 |
| Audience | 独立开发者、AI/开发工具团队、OSS 维护者 |
| Brand color | `#2d6dc3` |
| Accent color | `#fad13b` |
| Font | Source Han Sans SC / Noto Sans SC / 思源黑体 |
| Contact email | `hello@ricoui.com` |
| Repository | `https://github.com/ricocc/ricoui-saas-template` |

## 已实现范围

- 基于 Astro 6.4 的静态 SaaS 营销站。
- `src/styles/global.css` 中的 Tailwind CSS v4 token 系统。
- 全站中文文案和中文主 README。
- 全站字体统一为思源黑体字体栈。
- 支持浅色 / 深色模式，并持久化用户偏好。
- 基于 Astro Content Layer 的 MDX Blog 和 Changelog。
- 可复用 section、UI、card、layout 和 widget 组件。
- SEO 基础：Meta、Open Graph、sitemap、RSS、robots.txt、canonical URL。
- Demo 联系表单，仅有本地 UI 行为。
- Demo 登录和注册页面。
- 移动端、平板和桌面端响应式布局。

## 技术栈

| Area | Implementation |
| --- | --- |
| Framework | Astro 6.4 |
| Build tooling | Vite 7.3 |
| Styling | Tailwind CSS v4, CSS custom properties, `@theme` tokens |
| Content | MDX, `@astrojs/mdx`, Astro Content Layer |
| Icons | `@lucide/astro` |
| Motion | AOS, CSS animation, `motion` dependency |
| SEO | `@astrojs/sitemap`, `@astrojs/rss`, custom meta components |
| Type safety | TypeScript, `astro check` |
| Code quality | Biome |
| Images | Static assets, `sharp` |

## 路由

| Route | 用途 | Source |
| --- | --- | --- |
| `/` | SaaS 首页 | `src/pages/index.astro` |
| `/features` | 功能详情 | `src/pages/features.astro` |
| `/pricing` | 价格示例页 | `src/pages/pricing.astro` |
| `/blog` | Blog 列表 | `src/pages/blog/index.astro` |
| `/blog/[slug]` | Blog 文章页 | `src/pages/blog/[...slug].astro` |
| `/blog/page/[page]` | Blog 分页 | `src/pages/blog/page/[page].astro` |
| `/changelog` | 版本记录 | `src/pages/changelog.astro` |
| `/about` | 项目介绍 | `src/pages/about.astro` |
| `/contact` | Demo 联系页 | `src/pages/contact.astro` |
| `/elements` | 组件和设计系统参考 | `src/pages/elements.astro` |
| `/sign-in` | 登录模板 | `src/pages/sign-in.astro` |
| `/sign-up` | 注册模板 | `src/pages/sign-up.astro` |
| `/signin` | 居中登录模板 | `src/pages/signin.astro` |
| `/signup` | 居中注册模板 | `src/pages/signup.astro` |
| `/rss.xml` | RSS feed | `src/pages/rss.xml.js` |
| `/404` | 404 页面 | `src/pages/404.astro` |

## 页面要求

### Home

首页展示 RicoFast 的核心价值、问题场景、设计系统、功能、产品预览、使用场景、技术栈、价格示例、FAQ、最新文章和最终 CTA。

### Features

功能页展开页面结构、section 组件、MDX 内容、动效、性能和 token 化设计系统。

### Pricing

价格页是模板示例内容，不代表 RicoFast 真实收费。包含 Free、Pro、Enterprise 示例套餐、计费切换、对比表、FAQ 和 CTA。

### Blog / Changelog

Blog 和 Changelog 都来自 MDX 内容集合，示例内容已改为中文。Blog 支持 frontmatter、图片、精选文章和分页。

### Auth Pages

Auth 页面是静态模板屏幕，包含本地 demo 状态，不连接真实认证服务。

### Contact

联系页提供静态表单和本地成功状态。上线前需要接入 Resend、Formspree、Cloudflare Forms 或自有 API。

## 内容集合

Blog 目录：`src/content/post/`

Changelog 目录：`src/content/changelog/`

schema 定义在 `src/content.config.js`。英文技术字段如 `title`、`description`、`publishDate`、`featured` 保持不变。

## 设计系统

主要文件：

- `src/styles/global.css`
- `docs/DESIGN.md`
- `tailwind.config.mjs`

当前规则：

- 全站字体使用 `Source Han Sans SC`, `Noto Sans SC`, `思源黑体`。
- 主色为 `#2d6dc3`，强调色为 `#fad13b`。
- 浅色页面底为 `#fdfaf5`，深色页面底为 `#0b1220`。
- 动效保持克制，并遵循 `prefers-reduced-motion`。
- 常规 section 使用 `.site-container`，窄内容使用 `.inner-container`。

## 构建和 QA

支持命令：

```bash
pnpm dev
pnpm build
pnpm preview
pnpm check
pnpm astro
```

发布前建议验证：

- `pnpm build`
- `pnpm check`
- 主要页面人工浏览
- 浅色 / 深色模式
- 移动端和桌面端布局
- 设置 `PUBLIC_SITE_URL` 后检查 sitemap 和 RSS

## 相关文档

- `docs/DESIGN.md`：设计系统。
- `docs/PLAN.md`：项目概览。
- `docs/plan/`：页面级记录。
- `README.md`：中文主文档。
