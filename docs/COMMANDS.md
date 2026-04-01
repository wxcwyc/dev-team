# COMMANDS.md — 常用命令速查（workspace-dev-team）

> 目标：降低沟通成本。遇到问题先按这里收集信息，再交给 Support Triage 分诊。

## 通用（任何项目）

- 查看目录结构：
  - `ls -la`
- 搜索关键字（日志/配置）：
  - `rg "keyword" -n .`
- 查看环境变量样例：
  - `cat .env.example`

## Node.js（后端）

- 安装依赖：`npm i`
- 开发启动（常见）：`npm run dev`
- 生产启动（常见）：`npm start`
- 运行测试（常见）：`npm test`

## React（前端）

- 安装依赖：`npm i`
- 开发启动（常见）：`npm run dev`
- 构建（常见）：`npm run build`

## Docker / Compose

- 启动：`docker compose up -d`
- 关闭：`docker compose down`
- 看日志：`docker compose logs -f --tail=200`
- 重建：`docker compose up -d --build`

## MongoDB（常见排查）

- 查看容器状态：`docker ps`
- 查看 Mongo 日志：`docker compose logs -f mongo --tail=200`
- 检查端口占用：
  - `lsof -i :27017`

## OpenClaw / workspace 自检

- 确认事实源：`ls -la projects/<slug>/`
- 确认调度规则：`ls -la skills/agency-dev-team/ROUTING.md`

---

## 复制给 Support Triage 的“最小信息集”（建议）

请尽量提供：
- 你运行的命令（原样粘贴）
- 报错全文（前 50 行 + 末尾 50 行）
- `docker compose logs -f --tail=200`（若使用 compose）
- 你的系统与 Node 版本（`node -v`）
