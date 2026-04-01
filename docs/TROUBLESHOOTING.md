# TROUBLESHOOTING.md — 常见问题与排障（workspace-dev-team）

> 目标：把“可预期的坑”提前写成 runbook，Support Triage 会持续更新这份文档。

## 1) Mongo 连接失败（本地 / Docker Compose）

### 症状
- 后端启动时报：`ECONNREFUSED 127.0.0.1:27017`
- 或认证失败：`Authentication failed`

### 先做这 5 步（最短路径）
1. `docker ps`（确认 mongo 容器是否在跑）
2. `docker compose logs -f mongo --tail=200`（看 mongo 是否启动失败）
3. `lsof -i :27017`（是否端口冲突）
4. 检查后端连接串（env）：host 是否写成 `localhost` 还是 `mongo`（compose 网络里通常用服务名 `mongo`）
5. 若启用了账号密码：确认用户名/密码/认证库（`authSource`）一致

### 常见原因
- Mongo 容器未启动或 crash loop
- 连接串在 compose 网络内使用了 `localhost`
- 端口 27017 被占用
- 用户/密码配置不一致

### 收集信息（发给 Support Triage）
- 后端报错全文
- `docker ps`
- `docker compose logs -f mongo --tail=200`
- `.env`（可打码敏感信息，但保留 key/结构）

---

## 2) 前端请求后端报 CORS

### 症状
- 浏览器控制台提示 CORS blocked

### 处理
- 后端加 CORS 允许来源（dev 环境允许 `http://localhost:<port>`）
- 或前端 dev server 配置 proxy（推荐）

---

## 3) 环境变量缺失/加载失败

### 症状
- 启动时报某某 env 未定义

### 处理
- 对照 `.env.example` 补齐 `.env`
- 确认运行命令是否加载了 env（例如 dotenv）

---

## 4) Docker Compose 起不来

### 处理
- `docker compose logs -f --tail=200`
- `docker compose down -v`（慎用：会清 volume）
- 检查 Docker Desktop 是否运行

---

## 维护约定（强制）

- 每次 Support Triage 处理完一个问题：
  1) 必须补一条到本文件（或扩展已有条目）
  2) 给出“症状 / 最短路径 / 常见原因 / 收集信息”四段

---

## 质量门禁（支持视角）

当问题被关闭（close）前，至少满足：
- 复现步骤明确且可重复
- 修复方案有验证步骤
- 本文档已有对应 runbook 条目更新（或确认已有条目已覆盖）
