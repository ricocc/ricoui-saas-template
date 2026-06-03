# RicoFast - 面向 Astro 的高质感 SaaS 模板


RicoFast 是一个开源 SaaS 官网模板，基于 Astro 6 和 Tailwind CSS v4 构建。它适合独立开发者、AI/开发工具团队、开源项目维护者，用来快速搭建一个设计完成度更高的产品站。

![preview](/docs/screenshot.jpeg)

![Astro](https://img.shields.io/badge/Astro-6.4.2-FF5D01?logo=astro&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7.3.3-646CFF?logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.1.14-38B2AC?logo=tailwind-css&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

**链接：** [在线演示](https://ricofast.pages.dev/) · [GitHub](https://github.com/ricocc/ricoui-saas-template) · [Changelog](https://ricofast.pages.dev/changelog) · [Elements](https://ricofast.pages.dev/elements)

## 为什么是 RicoFast

很多 SaaS 模板要么太像 starter，真正上线前还要补大量页面；要么过于臃肿，功能很多但设计质量不稳定。RicoFast 的优势是专注于设计和审美，提供供一个能继续扩展的设计系统：预置常用页面、可复用组件、MDX 内容系统、暗黑模式和写进 `docs/DESIGN.md` 的设计规范。

中文版本已统一使用思源黑体字体栈：`Google Sans`、`Noto Sans SC`、`思源黑体`。

## 特性

- **11 个页面**：Home、Features、Pricing、Blog、Changelog、About、Contact、Sign in、Sign up、Elements、404
- **15+ 可复用 section**：Hero、FeatureGrid、Pricing、FAQ、Steps、Tech stack、Use cases、FinalCTA 等
- **Auth 页面模板**：登录 / 注册页面包含分屏和居中卡片两种样式
- **MDX Blog & Changelog**：基于 Astro Content Layer
- **暗黑模式**：class-based，加载时避免闪烁
- **设计系统**：颜色、字体、间距和动效 tokens 记录在 `docs/DESIGN.md`
- **响应式布局**：覆盖 375 / 768 / 1024 / 1440 常见断点
- **SEO 基础**：Open Graph、Twitter cards、sitemap、RSS feed
- **TypeScript**：构建时运行 `astro check`
- **MIT 协议**：个人和商业项目均可使用

## 技术栈

- **Framework:** [Astro 6.4.2](https://astro.build)
- **Build tooling:** [Vite 7.3](https://vite.dev/)
- **Styling:** [Tailwind CSS v4.1](https://tailwindcss.com) + `@theme`
- **Content:** MDX + `@astrojs/mdx`
- **Animation:** [AOS](https://michalsnik.github.io/aos/) + [motion.js](https://motion.dev/)
- **Icons:** [Lucide](https://lucide.dev/) via `@lucide/astro`
- **Code quality:** TypeScript + Biome

## 环境要求

- Node.js `>=22.12.0`
- pnpm `>=9`

## 快速开始

```bash
git clone https://github.com/ricocc/ricoui-saas-template.git my-saas
cd my-saas
pnpm install
pnpm dev
```

开发服务器默认运行在 `http://localhost:5200`。

## 环境变量

复制 `.env.example` 为 `.env`，并设置你的域名：

```env
PUBLIC_SITE_URL=https://your-domain.com
PUBLIC_GA4_ID=your-google-analytics-id  # 可选
PUBLIC_UMAMI_ID=your-umami-id            # 可选
```

上线前建议设置真实的 `PUBLIC_SITE_URL`，否则 sitemap、RSS 和 canonical URL 会使用默认值。

## 项目结构

```text
docs/
  DESIGN.md           # 设计 tokens、字体、间距和动效规则
  PLAN.md             # 项目概览
  PRD.md              # 当前实现范围
public/
  assets/             # 图片、图标、logo、og.jpg
src/
  pages/              # Astro 路由页面
  layouts/            # Layout、PageLayout、PostLayout、Meta
  components/         # sections、ui、cards、widgets 等组件
  collections/        # menu.json、social.json、stack.json
  content/            # Blog 和 Changelog MDX
  config/site.js      # 站点信息、SEO、社交链接
  styles/global.css   # Tailwind v4 @theme tokens
```

## 常用命令

```bash
pnpm dev       # 本地开发
pnpm build     # astro check && astro build
pnpm preview   # 预览生产构建
pnpm check     # Biome 检查和格式化
```

## 首先改哪里

1. `src/config/site.js`：站点名、作者、邮箱、SEO 元信息和社交链接。
2. `src/styles/global.css`：品牌色、强调色、字体 tokens。中文版本默认使用思源黑体。
3. `src/collections/menu.json`：导航菜单。
4. `src/pages/index.astro`：首页 Hero、功能、价格和 FAQ 文案。
5. `src/content/post/` 与 `src/content/changelog/`：替换示例文章和版本记录。
6. `public/og.jpg`、`public/assets/logo.png`：替换品牌资产。

## 文档

- [`docs/DESIGN.md`](docs/DESIGN.md)：设计系统与 tokens
- [`docs/PRD.md`](docs/PRD.md)：当前产品范围
- [`docs/PLAN.md`](docs/PLAN.md)：项目概览
- [`docs/plan/`](docs/plan/)：页面级实现记录
- [`CLAUDE.md`](CLAUDE.md)：AI 编程助手上下文

## 部署

构建产物是静态文件，任何静态托管平台都可以部署。

| 平台 | 构建命令 | 输出目录 |
| --- | --- | --- |
| Cloudflare Pages | `pnpm build` | `dist/` |
| Vercel | `pnpm build` | `dist/` |
| Netlify | `pnpm build` | `dist/` |
| GitHub Pages | `pnpm build` + Pages action | `dist/` |

## License

[MIT](LICENSE)
