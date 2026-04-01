# DECISIONS.md — demo

> 规则：每条决策一段，写清“选了什么、为什么、替代方案、后果”。

## 2026-03-29 技术栈与工程形态

- 决策：React（前端）+ Node.js（后端）+ MongoDB（数据库）；优先提供 Docker Compose 本地一键启动。
- 背景：用户明确指定该栈；目标是快速跑通 MVP，并保留扩展性。
- 选择原因：生态成熟、上手快、适合 demo；Mongo 便于快速建模。
- 替代方案：Postgres；或后端选 Fastify / NestJS；前端选 Next.js。
- 影响与代价：Mongo 的 schema 约束弱，需要在代码层做校验；后续可再引入更严格的 validation。
- 验证方式：新环境 clone 后按 README 一键启动；CRUD + 前端交互验收通过。
