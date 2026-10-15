# data 目录说明

`data/stars.json` 是本项目在 `main` 分支中的增量数据源，用于：

- 记录已处理过的仓库及其 AI 摘要，实现增量更新，避免每次全量重新生成。
- 作为本地同步脚本运行时的数据缓存。

说明：

- GitHub Actions 每次运行完成后，会将更新后的 `data/stars.json` 自动提交回 `main`（内容无变化时跳过提交），保证增量状态持久化。
- 站点发布使用 GitHub 官方 artifact 方式，产物中的 `data/stars.json` 供前端页面读取，不再依赖 `gh-pages` 分支。
- 若你希望从零重建数据集，可手动运行 Action 并选择 `force_rebuild=true`。
