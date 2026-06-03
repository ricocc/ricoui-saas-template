# RicoFast 项目概览

> 最后更新：2026-06-02

RicoFast 是一个 static-first SaaS 官网模板，基于 Astro、Tailwind CSS v4、MDX 和可复用组件系统构建。当前项目已调整为中文项目，界面文案和文档以中文为主，技术名、文件名和工具名保留英文。

## 定位

一个面向中文 SaaS、AI 工具、开发者工具和开源项目的高质感官网模板。

## 目标用户

- 独立开发者
- 早期创业团队
- AI 产品团队
- 开发者工具团队
- 开源项目维护者
- 需要快速发布产品站的设计师和工程师

## 技术栈

- Astro 6.4
- Vite 7.3
- Tailwind CSS v4
- MDX
- TypeScript
- AOS
- motion
- Lucide icons
- Astro RSS and sitemap integrations

## 已实现页面

| 页面 | 路由 | 用途 |
| --- | --- | --- |
| Home | `/` | SaaS 官网首页 |
| Features | `/features` | 功能详情 |
| Pricing | `/pricing` | 价格示例页 |
| Blog | `/blog` | MDX 文章列表 |
| Blog detail | `/blog/[slug]` | MDX 文章详情 |
| Changelog | `/changelog` | 版本记录 |
| About | `/about` | 项目介绍与价值观 |
| Contact | `/contact` | Demo 联系表单 |
| Elements | `/elements` | 组件与设计系统参考 |
| Sign in | `/sign-in` | Auth 登录模板 |
| Sign up | `/sign-up` | Auth 注册模板 |
| RSS | `/rss.xml` | Blog RSS feed |
| 404 | `/404` | 页面未找到 |

仓库中还保留 `/signin` 与 `/signup` 两个居中卡片版本。

## 主要定制文件

- `src/config/site.js`：站点信息、SEO、社交链接。
- `src/styles/global.css`：设计 tokens、思源黑体字体栈、暗黑模式变量。
- `src/collections/menu.json`：导航。
- `src/collections/social.json`：社交数据。
- `src/collections/stack.json`：技术栈数据。
- `src/content/post/`：Blog MDX。
- `src/content/changelog/`：Changelog MDX。
- `public/`：logo、favicon、OG 图和静态资源。

## 文档地图

- `docs/PRD.md`：当前产品范围。
- `docs/DESIGN.md`：设计系统参考。
- `docs/plan/`：页面级记录。
- `README.md`：中文主文档。
- `README-zh.md`：旧中文入口兼容文件。
