# context-strategy

全局上下文/记忆策略（借鉴 OpenViking）：分层（L0/L1/L2）+ 按需加载 + 可追溯落盘。

## 目标

- 降低 token 噪音与遗忘
- 让“关键结论”永远可在文件中找到
- 让多代理协作有统一的上下文入口

## 分层规则（硬约束）

### L0：入口与导航（永远优先）
- `BOOT.md` / `SOUL.md` / `START_HERE.md` / `projects/_index.md`

### L1：项目可执行记忆（选定项目后必须）
- `projects/<slug>/SUMMARY.md`
- `projects/<slug>/PROJECT.md`
- `projects/<slug>/DECISIONS.md`
- `projects/<slug>/HANDOFF.md`

### L2：细节与证据（按需）
- `docs/COMMANDS.md` / `docs/TROUBLESHOOTING.md`
- `references/**`
- 日志/长输出/外部资料

## 读取顺序（强制建议）

- 未指定项目：只读 L0，必要时询问 `<slug>`
- 已指定项目：先读 `SUMMARY.md`，再按需读 PROJECT/DECISIONS/HANDOFF

## 写入/落盘规则（强制）

- 关键决策 → `projects/<slug>/DECISIONS.md`（并同步更新 SUMMARY 的“现行约定”）
- 阶段推进/下一步 → `projects/<slug>/HANDOFF.md`（并同步更新 SUMMARY 的 TL;DR/Next）
- 重复排障问题 → `docs/TROUBLESHOOTING.md`
- 可复用流程/清单 → 升级为 `skills/<name>/SKILL.md` 或 `skills/agency-dev-team/templates/*.md`

## 触发器（何时强制做摘要）

满足任一条件，应更新 `projects/<slug>/SUMMARY.md`：
- 本轮讨论产生 ≥1 条关键决策
- 任务拆分 ≥3 个子任务包且存在依赖
- 进入/完成里程碑（M1/M2）
- 出现阻塞（Blocker）或状态变黄（Yellow/Red）

## 参考

- 一页纸策略：`references/strategy/context-memory.md`
