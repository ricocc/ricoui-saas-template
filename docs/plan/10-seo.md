# 10 SEO

SEO 元信息主要来自 `src/config/site.js` 和各页面的 `Layout` props。

## 当前规则

- 默认 title 和 description 已中文化。
- keywords 使用中文 SaaS / Astro / Tailwind 等关键词。
- Blog 和 Changelog 内容已改为中文。
- 日期格式使用 `zh-CN`。

## 上线前

- 设置 `PUBLIC_SITE_URL`。
- 替换 `public/og.jpg`。
- 检查 `rss.xml` 和 sitemap 输出。
