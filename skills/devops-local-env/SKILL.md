# devops-local-env

本地环境与一键启动技能：让任何人 clone 后能稳定跑起来。

## 适用场景
- 新项目骨架
- 新同事/新代理接手
- demo 交付前

## 输出（必须包含）
- 启动方式：最短路径（3-6 步）
- 环境变量：`.env.example` + 缺省值策略
- 依赖：Docker/Node 版本要求
- 常见坑：追加到 `docs/TROUBLESHOOTING.md`

## 检查清单（最小）
- [ ] `docker compose up -d` 可启动依赖（db/cache 等）
- [ ] `npm i` / `pnpm i` 可安装
- [ ] 后端/前端 dev server 可启动
- [ ] health check 可访问
- [ ] README 可复现

## 参考（武器库）
- `references/lobehub/docker-compose/`
- `references/lobehub/.env.example`
