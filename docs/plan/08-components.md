# 08 Components

组件应优先沿用现有结构。

## 组件组

- `sections/`：页面级 section，如 Header、Footer、Pricing、FAQ。
- `ui/`：小型复用组件，如 Button、Badge、BrowserFrame、PricingToggle。
- `cards/`：重复卡片，如 BlogCard、TechStackCard。
- `widgets/`：页面工具，如 Toc、Pagination、ToTop。
- `elements/`：PageHeader、SectionHeader、SeparatorLine。

## 规则

- 中文可见文案写在页面或数据数组中。
- 组件 API 和文件名保留英文。
- 新组件必须兼容浅色和深色模式。
