# 参与贡献

感谢你愿意参与 RicoFast。Bug 反馈、功能建议、文档修正和代码贡献都欢迎。

## 报告 Bug

提交 issue 前，请先搜索现有 [Issues](https://github.com/ricocc/ricoui-saas-template/issues)。新 issue 建议包含：

- 问题描述
- 复现步骤
- 期望行为和实际行为
- 截图或录屏
- 环境信息：浏览器、操作系统、Node.js 版本

## 提出功能建议

请说明：

- 这个功能解决什么问题
- 适合放进模板本体，还是更适合作为示例
- 可能的实现方式

## 提交代码

```bash
git clone https://github.com/your-username/ricoui-saas-template.git
cd ricoui-saas-template
git checkout -b feature/your-feature-name
pnpm install
```

开发时请参考：

- [`docs/DESIGN.md`](docs/DESIGN.md)
- [`docs/PRD.md`](docs/PRD.md)
- [`CLAUDE.md`](CLAUDE.md)

提交前运行：

```bash
pnpm check
pnpm build
```

## 代码约定

- 使用 Astro Content Layer：`getCollection()`、`entry.id`、`render(entry)`。
- 样式优先使用 `src/styles/global.css` 中的 tokens。
- 全站字体保持思源黑体字体栈。
- 新组件必须同时考虑浅色和深色模式。
- 动效优先使用 AOS，复杂编排再使用 motion.js。
- 不要为了简单 UI 行为引入新依赖。
- Auth 和 Contact 页面是静态 demo，不要把它们写成真实后端能力。

## PR 前检查

- [ ] `pnpm check` 通过
- [ ] `pnpm build` 通过
- [ ] 已在本地 `pnpm dev` 检查
- [ ] 浅色 / 深色模式可用
- [ ] 移动端和桌面端布局正常
- [ ] 没有坏掉的 import 或过期链接

## 联系

- Issues: https://github.com/ricocc/ricoui-saas-template/issues
- Email: hello@ricoui.com
