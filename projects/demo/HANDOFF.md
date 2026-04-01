# HANDOFF.md — demo

## 这次交接的范围

创建 demo 项目的事实源文件与初始规划。

## 当前结论（TL;DR）

项目已按 agency-dev-team 的事实源规范初始化：已建立 `projects/demo/PROJECT.md | DECISIONS.md | HANDOFF.md`。下一步按 ROUTING 拆分后端/前端/QA/DevOps 任务包并开始实现。

## 已完成（Done）

- 创建 `projects/demo/` 目录
- 初始化 PROJECT/DECISIONS/HANDOFF 三件套

## 进行中（In Progress）

- 选择具体框架与目录结构（Express vs Fastify；Vite React）

## 待办（Next）

- 按 `skills/agency-dev-team/ROUTING.md` 拆 2-5 个子任务并分工
- 明确 API 合同（Todo/Notes 的字段、路由、错误码）
- 落地仓库结构与启动方式（npm scripts + docker compose）

## 关键决策与原因（链接到 DECISIONS.md）

- 技术栈与工程形态：见 `projects/demo/DECISIONS.md`

## 风险与坑

- 如果 mono-repo 结构定错，后续扩展会麻烦
- Mongo schema/validation 需要尽早统一

## 如何验证

- 本地运行：完成实现后提供 `README` 指令（docker compose + npm install + npm run dev）
- 测试命令：待补（至少 API 的基础测试）
- 验收标准：前端可完成对示例资源的 CRUD；后端 API 返回符合约定；错误处理一致
