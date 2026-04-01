# 2026-03-31 — 引入 dev-team 轻量 pipeline（P0+P1）

## 目标
借鉴 pskoett-ai-skills 的核心思想（pipeline / intent framing / context drift / post-completion quality pass / self-improvement），增强 dev-team 的多代理开发流程，但避免过度复杂与强依赖 hooks。

## 已落盘变更（实施完成）

### P0（在现有规范中落地）
1) `BOOT.md`
- 新增：**Pipeline 门禁（强制：先分级再执行）**
- 要求：收到任何“要做事”的请求先完成 Task Class 分级（Trivial/Small/Medium/Large/Long-running/Incident）
- 给出：流程深度建议与必须启用的门禁/工件

2) `skills/agency-dev-team/ROUTING.md`
- 新增：**执行意图门禁**（Intent Frame → 确认 → 执行）
  - 模板：`skills/agency-dev-team/templates/intent_frame.md`
  - 发现范围漂移：触发 Intent Check，确认是否 Pivot
- 新增：**完成后门禁**（Mini Simplify & Harden → Review）
  - non-trivial 变更先做 60 秒 Mini S&H，新增改动不超过原 diff 的 20%
  - 结构性重构需先提案并等确认
  - 之后进入评审双门禁：`spec-compliance-review` → `code-review`

3) `skills/agency-dev-team/templates/intent_frame.md`
- 新增：Intent Frame 固定模板，用于实现前意图契约

### P1（新增轻量编排器 skill）
4) `skills/skill-pipeline/SKILL.md`
- 新增：dev-team 轻量总编排器
- 功能：任务分级 + 门禁/工件路由 + 固定输出格式
- 设计：不依赖 hooks，作为 Dev Lead 开工前的强制流程（由 BOOT/ROUTING 约束执行）

## 使用约定
- 新任务/推进阶段时，先运行/遵循 `skills/skill-pipeline/SKILL.md` 的分级与路由输出。
- 进入实现前必须输出 Intent Frame 并获得确认。
- non-trivial 变更完成后必须先 Mini S&H，再进入 spec-compliance-review 与 code-review。

## 参考来源
- pskoett-ai-skills（skill-pipeline / intent-framed-agent / context-surfing / simplify-and-harden / self-improvement）
