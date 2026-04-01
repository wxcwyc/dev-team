# release_checklist.md — 发布/交付检查清单（Release Captain / Dev Lead）

> 目标：把“能跑”变成“可交付”。用于上线/交付 demo/发版。

## 1) 范围与版本
- [ ] 本次发布范围（链接到 PROJECT/HANDOFF）
- [ ] 版本号/Tag/Commit
- [ ] 回滚策略（如何回到上一版本）

## 2) 配置与环境变量
- [ ] `.env.example` 与实际配置一致（缺失项已补）
- [ ] 敏感信息不入库
- [ ] 数据库连接/第三方 key 已验证

## 3) 数据与迁移
- [ ] Mongo 集合/索引（如需要）
- [ ] 兼容性：旧数据是否可读

## 4) 后端
- [ ] /health 正常
- [ ] 核心 API 用例通过（至少 CRUD + 错误场景）
- [ ] 错误处理一致（错误码/消息结构）
- [ ] 日志关键字段齐全（request id/错误栈）

## 5) 前端
- [ ] 关键页面功能通过（CRUD、错误提示、loading）
- [ ] API baseUrl / proxy 配置正确
- [ ] 构建通过（`npm run build`）

## 6) 运行与监控（最小）
- [ ] README 启动步骤可复现（新环境 30 分钟内跑通）
- [ ] docker compose 可启动/停止
- [ ] 关键日志位置与排障入口（链接 docs/TROUBLESHOOTING）

## 7) 文档与交接
- [ ] 更新 `projects/<slug>/HANDOFF.md`（Done/In Progress/Next）
- [ ] 关键决策已写入 `DECISIONS.md`
- [ ] 已知风险/限制写清楚
