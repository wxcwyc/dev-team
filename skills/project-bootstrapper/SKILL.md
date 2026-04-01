# project-bootstrapper

一键初始化新项目骨架与事实源文件，配合 `agency-dev-team` 使用。

## 适用场景

- 你想快速创建 `projects/<slug>/` 三件套（PROJECT/DECISIONS/HANDOFF）
- 你想生成一个可运行的最小仓库骨架（前端/后端/数据库）
- 你不想每次手工复制模板与目录

## 输入

- slug（项目代号）
- 技术栈（例如：react + nodejs + mongodb）
- repo 形态（mono-repo / multi-repo）

## 输出/副作用

在当前 workspace 下创建/更新：

- `projects/<slug>/PROJECT.md`
- `projects/<slug>/DECISIONS.md`
- `projects/<slug>/HANDOFF.md`
- 更新 `projects/_index.md` 增加条目

可选：生成 repo 骨架目录（由用户确认后执行）：

- `<slug>/frontend/`（React）
- `<slug>/backend/`（Node.js）
- `<slug>/docker-compose.yml`（MongoDB）
- `<slug>/README.md`

## 使用范式

对主会话说：

- “用 project-bootstrapper 初始化项目 `<slug>`，栈为 React/Node/Mongo，mono-repo。”

然后主会话应：

1) 生成 facts（projects/<slug>）
2) 记录关键选型到 DECISIONS
3) 输出下一步拆分（按 agency-dev-team/ROUTING）

