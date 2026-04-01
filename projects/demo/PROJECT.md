# PROJECT.md — demo

## 项目代号（slug）

demo

## 一句话目标

做一个最小可用的全栈 demo：React 前端 + Node.js 后端 + MongoDB，提供一套可运行、可测试、可扩展的项目骨架与示例业务。

## 范围（做什么 / 不做什么）

做什么（MVP）：
- 单体仓库（或 mono-repo）即可一键启动：前端、后端、MongoDB
- 提供一个示例业务域（例如：Todo/Notes）
  - CRUD API（列表/创建/更新/删除）
  - 前端页面完成增删改查
- 基础工程化：配置、日志、错误处理、README、基础测试

不做什么（先不做）：
- 复杂鉴权/多租户/权限系统
- 完整的后台管理体系
- 高可用/多环境发布流水线（先提供本地 + 可选 docker compose）

## 技术栈（已定）

- Frontend：React
- Backend：Node.js（建议 Express 或 Fastify 二选一）
- Database：MongoDB
- Dev tooling：Docker Compose（可选但推荐），基础 lint/test

## 约束

- 目标：30 分钟内本地跑起来（新机器克隆后）
- 可维护：目录结构清晰、最少魔法

## 里程碑

- M1（骨架可跑）：初始化 repo；docker compose 起 Mongo；后端 health + CRUD；前端页面可访问并能读写
- M2（工程化）：补测试、错误处理、README、基础 CI（可选）

## 关键风险

- 技术栈选择分歧（Express vs Fastify；Vite vs CRA；ODM 选型）
- Mono-repo 目录规划影响后续扩展

## 负责人/子代理分工（将按 ROUTING 细化）

- Dev Lead：主会话
- Backend：Node.js API + Mongo 持久化
- Frontend：React UI + API 集成
- QA：测试清单 + 验收用例
- DevOps：docker compose / scripts（可选）
