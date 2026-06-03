# RicoFast Design System

本文档描述 RicoFast 当前实现的视觉系统。项目已中文化，所有 UI 字体统一使用思源黑体字体栈；`DESIGN.md`、tokens、组件名、工具名等英文标识保持英文，方便开发时查找。

## 设计方向

RicoFast 使用克制、清晰的 SaaS 产品站风格：

- 温暖浅色页面底。
- 蓝色主品牌色。
- 金色强调色。
- 统一的思源黑体排版。
- 虚线分隔和轻量卡片边框。
- 克制动效，不做装饰性堆叠。
- 支持 class-based dark mode。

## Source Files

- `src/styles/global.css`：tokens、全局样式、暗黑模式变量。
- `tailwind.config.mjs`：Tailwind 扫描范围和 dark mode 策略。
- `src/layouts/Layout.astro`：全局布局、样式导入、dark mode 启动脚本。
- `src/assets/js/main.js`：dark mode、Header、移动端菜单、AOS 初始化。

## Color Tokens

### Brand

| Token | Value | 用途 |
| --- | --- | --- |
| `--color-primary` | `#2d6dc3` | 品牌色、链接、CTA、标题 |
| `--color-primary-strong` | `#0066ff` | hover 和强调 |
| `--color-primary-light` | `#8fb9ff` | 浅色强调 |
| `--color-accent` | `#fad13b` | badge、高亮 |
| `--color-accent-light` | `#faeb75` | 柔和强调状态 |

### Background

| Token | Value | 用途 |
| --- | --- | --- |
| `--color-bg-primary` | `#fdfaf5` | 浅色页面底 |
| `--color-bg-secondary` | `#fff` | 卡片和面板 |
| `--color-bg-primary-light` | `#faf9f5` | 内容表面 |
| `--color-bg-primary-dark` | `#0b1220` | 深色页面底 |
| `--color-bg-secondary-dark` | `#0f1b2d` | 深色卡片和面板 |

### Text

| Token | Value | 用途 |
| --- | --- | --- |
| `--color-text-primary` | `#2d6dc3` | 浅色标题 |
| `--color-text-secondary` | `#3f4a5a` | 浅色正文 |
| `--color-text-tertiary` | `#7a6550` | 辅助信息 |
| `--color-text-primary-dark` | `#3884eb` | 深色标题 |
| `--color-text-secondary-dark` | `#c5cedb` | 深色正文 |
| `--color-text-tertiary-dark` | `#9bb3d7` | 深色辅助信息 |

## Typography

字体在 `src/styles/global.css` 中导入和声明。

| Token | Font | 用途 |
| --- | --- | --- |
| `--font-brand` | Source Han Sans SC / Noto Sans SC / 思源黑体 | 展示标题、Hero、section 标题 |
| `--font-sans` | Source Han Sans SC / Noto Sans SC / 思源黑体 | 正文、UI、导航、按钮 |
| `--font-body` | Source Han Sans SC / Noto Sans SC / 思源黑体 | 正文 |

规则：

- 全站字体使用思源黑体字体栈。
- 标题通过字号和字重建立层级，不再依赖 serif 字体。
- 不使用负 letter spacing 作为默认样式。
- 紧凑 UI 内的标题不要使用 Hero 级别字号。

## Layout Tokens

| Token/Class | Value | 用途 |
| --- | --- | --- |
| `--max-screen` | `1200px` | 主站宽度 |
| `--inner-screen` | `800px` | 文章和窄内容 |
| `.site-container` | max width + horizontal padding | 页面 section |
| `.inner-container` | inner max width + padding | 窄内容 |

## Dark Mode

- Tailwind config: `darkMode: "class"`。
- 初始状态在 `Layout.astro` 中提前执行，避免页面闪烁。
- 用户偏好存储在 `localStorage.dark_mode`。
- 切换逻辑在 `src/assets/js/main.js`。
- 颜色覆盖在 `global.css` 的 `html.dark` 中维护。

## Motion

- AOS 全局导入并在 `src/assets/js/main.js` 初始化。
- 自定义 AOS 样式在 `src/styles/aos-custom.css`。
- 产品预览、价格切换等局部动效使用组件级 CSS。
- 动效必须遵循 `prefers-reduced-motion`。

常用属性：

```html
data-aos="fade-up-xs"
data-aos-once="true"
```

## Core Components

| Component | Path | 作用 |
| --- | --- | --- |
| Header | `src/components/sections/Header.astro` | 主导航 |
| Footer | `src/components/sections/Footer.astro` | Footer 导航和社交链接 |
| HeroSection | `src/components/home/HeroSection.astro` | 首页 Hero |
| Pricing | `src/components/sections/Pricing.astro` | 价格卡和计费切换 |
| FAQ | `src/components/sections/FAQ.astro` | FAQ 折叠区块 |
| BlogSection | `src/components/sections/BlogSection.astro` | Blog 预览和列表 |
| Button | `src/components/ui/Button.astro` | CTA 和链接按钮 |
| Badge | `src/components/ui/Badge.astro` | 小标签 |
| AccordionItem | `src/components/ui/AccordionItem.astro` | FAQ 项 |
| PricingToggle | `src/components/ui/PricingToggle.astro` | 月付 / 年付切换 |
| BrowserFrame | `src/components/ui/BrowserFrame.astro` | 浏览器风格产品框 |

## UI Rules

- 优先使用现有组件，不急着新增抽象。
- 需要图标时优先使用 `@lucide/astro`。
- CTA 使用 `Button.astro`。
- 产品预览使用 `BrowserFrame.astro`。
- 卡片保持克制：轻边框、低阴影、清楚间距。
- 新表面必须同时考虑浅色和深色模式。
- 优先使用 token，不在组件中随手写新颜色。
- 表单控件必须有 label、focus state 和清楚的成功/错误状态。

## Assets

- `public/og.jpg`
- `public/favicon.png`
- `public/assets/logo.png`
- `public/assets/icon/*`
- `public/assets/folder/*`
- `public/assets/stack/*`
- `public/assets/article-cover.jpg`
- `public/rico/*`

适配真实产品时，请替换这些品牌和内容资产。
