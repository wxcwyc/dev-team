# START_HERE — agency-dev-team（最短用法）

## 0) 先选一个项目 slug
例如：`demo-api`、`my-app`。

## 1) 新建项目事实源（只做一次）
- 建目录：`projects/<slug>/`
- 复制模板：
  - `skills/agency-dev-team/templates/project_brief.md` → `projects/<slug>/PROJECT.md`
  - `skills/agency-dev-team/templates/decision_log.md` → `projects/<slug>/DECISIONS.md`
  - `skills/agency-dev-team/templates/handoff.md` → `projects/<slug>/HANDOFF.md`
- 更新索引：`projects/_index.md`

## 2) 在 Dev Lead 主会话发起（每个阶段都可用）
把这句话发给主会话：

> 按 agency-dev-team 启动项目 `<slug>`：读取 `projects/<slug>/PROJECT.md`，按 `skills/agency-dev-team/ROUTING.md` 拆 2-5 个子任务并分工；每个任务给交付物+验收标准；关键决策写入 `DECISIONS.md`；阶段推进更新 `HANDOFF.md`。

## 3) 每次推进后的收敛动作（强制）
- 把“下一步 TODO + 风险/依赖”写入 `HANDOFF.md`
- 把“关键取舍”写入 `DECISIONS.md`

## 4) 扩展角色（按需）
- 在 `references/agency-agents/roles/` 找到需要的角色文件
- 精选复制到 `skills/agency-dev-team/souls/`
- 在 `skills/agency-dev-team/ROUTING.md` 加一条路由规则
