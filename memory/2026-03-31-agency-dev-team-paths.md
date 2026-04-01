# 2026-03-31 — agency-dev-team 事实源路径与同步策略

## 背景
在 dev-team workspace 中同时存在两份 `agency-dev-team`：
- `/Users/gawin/.openclaw/workspace-dev-team/skills/agency-dev-team`（增强版）
- `/Users/gawin/.openclaw/workspace/skills/agency-dev-team`（旧版/基础版，后被更新）

导致会话在读取 ROUTING/templates/souls 时发生“读错目录/不一致”的疑惑。

## 结论（永久规则）
1) **唯一事实源**：以 dev-team workspace 为准：
   - BOOT：`/Users/gawin/.openclaw/workspace-dev-team/BOOT.md`
   - agency-dev-team（ROUTING/templates/souls）：`/Users/gawin/.openclaw/workspace-dev-team/skills/agency-dev-team/`

2) **主 workspace 使用软链接统一**：
   - `/Users/gawin/.openclaw/workspace/skills/agency-dev-team` 被替换为软链接 → 指向 dev-team 增强版目录。
   - 备份目录：`/Users/gawin/.openclaw/workspace/skills/agency-dev-team.bak-20260331-075426`

3) **文件已修正（路径指向）**：
   - `workspace-dev-team/SOUL.md`：明确启动先读本 workspace 的 `BOOT.md`；并把 agency-dev-team 规范来源改为 dev-team 路径（而不是主 workspace）。
   - `workspace-dev-team/AGENTS.md`：把能力来源/ROUTING/ROLES 改为 dev-team 路径，并增加 BOOT 路径说明。

4) **两份目录不一致的事实**（修正前）：
   - dev-team 版 `ROUTING.md` 增强：SUMMARY 分层记忆门禁、Spec→Plan→Execute 阶段门禁、Support→Debug→Runbook、planning-with-files 3-file pattern、工程门禁（先读对应 skill）。
   - dev-team 版新增 templates：`project_summary.md/task_plan.md/findings.md/progress.md/support_runbook.md/release_checklist.md/status_report.md/api_test_minset.md` 等；新增 souls：`chief-of-staff.md/support-triage.md`。

## 术语澄清（防混淆）
- **角色（roles/roster）**：主要来源于 `skills/agency-dev-team/souls/*.md`，由 `ROUTING.md` 决定什么时候指派。
- `workspace-dev-team/skills/` 下的其他 skills 多为**流程/方法论技能**（如 code-review/testing/api-contract 等），通常由 `ROUTING.md` 的工程门禁在特定场景显式要求“先读再执行”。
- 平台注入的 `available_skills`（weather/tavily 等）是另一套机制，不等同于本地 skills 目录。

## 操作准则
- 每次开工/切项目：先读 `workspace-dev-team/BOOT.md`。
- 需要 ROUTING/templates/souls 时：只读 dev-team skill 目录（主 workspace 通过软链接等价）。
- 避免维护双份拷贝；如需回滚主 workspace 的软链接，使用备份目录恢复。
