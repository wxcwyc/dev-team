# SUMMARY.md 模板（项目可执行摘要 / L1）

> 目标：把项目当前状态压缩成“能推进”的最小上下文。任何人/代理只读这份就能接着干。

## TL;DR（1-5 句）

已初始化 demo 项目事实源（React + Node.js + MongoDB）。当前处于“实现前的选型与目录结构拍板”阶段：需要确定示例业务域（Todo/Notes）、repo 形态（mono-repo/双仓）与后端框架（Express/Fastify），然后即可并行推进后端 API、前端 UI、DevOps 一键启动与 QA 验收。

## 当前状态（Green/Yellow/Red）
- 状态：Yellow
- 理由：事实源齐全但实现尚未开始；关键选型与 API 合同未落盘，会阻塞并行开发。

## 里程碑与关键路径
- M1：骨架可跑（Mongo + 后端 health/CRUD + 前端 CRUD 页面联调）
- M2：工程化（测试、README、排障手册、发布/交付检查清单）
- Critical Path：先定 repo 结构与 API 合同 → 前后端并行实现 → docker compose/README 一键启动 → 验收用例

## Decisions Needed（需要拍板）
1) 示例业务域：Todo 还是 Notes？（推荐 Todo）
2) Repo 形态：mono-repo 还是双仓？（推荐 mono-repo）
3) 后端框架：Express 还是 Fastify？（推荐 Express）

## Blockers（阻塞）
- API 合同未定（字段/路由/错误结构）→ 阻塞前端联调
- repo 结构/启动方式未定 → 阻塞 DevOps 一键启动与 README

## Top Risks（Top 3）
1) 选型久拖导致实现反复（缓解：今天内拍板并写入 DECISIONS）
2) Mongo 校验策略不统一导致字段漂移（缓解：后端引入最小校验并在合同写清）
3) 本地启动不可复现（缓解：按 devops-local-env 清单完成 README+compose）

## Now（当前在做）
- 建立分层记忆：新增 `projects/demo/SUMMARY.md` 并补齐项目现状

## Next（下一步 3-7 条可执行 TODO）
1) 拍板 3 个决策（Todo/Notes；mono-repo/双仓；Express/Fastify）并更新 `DECISIONS.md`
2) 使用 `skills/api-contract/SKILL.md` 输出 API 合同草案并落盘（docs 或 DECISIONS 摘要）
3) 后端实现：/health + CRUD + Mongo 持久化
4) 前端实现：CRUD 页面 + 错误/加载状态 + API 集成
5) DevOps：docker compose + README 一键启动（参照 `skills/devops-local-env/SKILL.md`）
6) QA：最小验收 checklist（参照 `skills/testing/SKILL.md`）

## 现行约定（接口/目录/运行方式等）
- 事实源：PROJECT/DECISIONS/HANDOFF/SUMMARY 均在 `projects/demo/`
- 排障沉淀：`docs/TROUBLESHOOTING.md`

## 最近更新
- 2026-03-29：初始化事实源 + 引入分层记忆 SUMMARY
