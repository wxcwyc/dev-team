# ROUTING（任务路由）— agency-dev-team

> 目的：让 Dev Lead 能把“开发→上线→运营”的工作稳定拆给合适的子角色，并收敛成项目事实源文件。

## 总规则

- Dev Lead 负责：澄清 → 拆分 → 指派 → 评审 → 收敛 → 落盘。
- 子角色输出的关键结论，必须被 Dev Lead 写入：
  - `projects/<slug>/PROJECT.md`（目标/范围/里程碑）
  - `projects/<slug>/DECISIONS.md`（技术/产品取舍）
  - `projects/<slug>/HANDOFF.md`（阶段交接/下一步）

## 分层记忆门禁（强制：选定项目后先读 SUMMARY）

一旦用户/Dev Lead 选定项目 `<slug>`，任何角色在开始执行前必须：

1) 读取 `projects/<slug>/SUMMARY.md`
2) 若 SUMMARY 信息不足，再按需读取 `PROJECT.md / DECISIONS.md / HANDOFF.md`

若 `SUMMARY.md` 不存在：
- Dev Lead 必须按模板创建（`skills/agency-dev-team/templates/project_summary.md`）

> 规则：未遵循该顺序导致的“重复提问/遗漏关键约定/偏离当前计划”，视为不合格输出。

## 阶段门禁（强制：Spec → Plan → Execute → Review → Release）

当用户请求“开始做/进入实现”时，Dev Lead 必须确保已完成：

1) **Spec**：需求与范围已写入 `PROJECT.md`；关键取舍已写入 `DECISIONS.md`
2) **Plan**：已拆分 2-5 个子任务包（若任务 ≥3 且有依赖，必须引入 PM 总控输出状态与依赖）
3) **Execute**：每个任务包都包含 Deliverables + Acceptance + Risks/Deps

> 若上述任一缺失：必须先补齐落盘，再进入实现。

## 执行意图门禁（强制：Intent Frame → 确认 → 执行）

当用户明确表示“开始做/进入实现/写代码/落地”时，Dev Lead 在任何实现动作前必须输出一份 **Intent Frame** 并获得确认。

模板：`skills/agency-dev-team/templates/intent_frame.md`

规则：
- Intent Frame 必须短（每项 1-2 句），可被人快速审核。
- 若用户不同意/调整：先更新 Intent Frame，再进入执行。
- 执行中若发现范围漂移：必须触发一次 Intent Check（对照 Outcome/Constraints），请用户确认是否 Pivot。

> 目标：把“隐含意图”显式化，降低 scope creep 与返工。

## 完成后门禁（强制：Mini Simplify & Harden → Review）

当一次实现产生 **non-trivial 变更**（触及可执行源码，且 ≥10 行逻辑变更，或涉及鉴权/校验/并发/数据访问等高风险逻辑）时：

1) 先执行 **Mini Simplify & Harden（S&H）**（60 秒心智预算，且新增改动不超过原 diff 的 20%）：
   - Simplify：去掉 debug/无用代码、改善命名、简化控制流（默认只做 cosmetic；结构性重构必须先提案并等确认）
   - Harden：补齐输入校验、错误处理、鉴权/权限、敏感信息日志、注入/路径风险
   - Document：最多新增 5 条“为什么这样写”的微注释（不是写文档）
2) 再进入评审双门禁（强制顺序）：
   - `skills/spec-compliance-review/SKILL.md` → `skills/code-review/SKILL.md`

> 目标：利用“刚写完的峰值上下文”做一次轻量自检，提升交付质量，减少评审返工。

## 故障升级门禁（强制：Support → Debug → Runbook）

当出现“启动失败/报错/500/超时/连不上”等问题时：

1) 先进行 **Support Triage**（分诊/归因/分派/验证）
2) 若仍无法确定根因或问题重复出现，升级为 **Systematic Debugging**（证据链 + 最小实验）
3) 无论是否修复，必须把结论沉淀为 runbook，更新 `docs/TROUBLESHOOTING.md`

> 规则：未更新 runbook 的排障输出视为未完成。

## 任务级计划门禁（强制：planning-with-files 3-file pattern）

当 Dev Lead/任意角色决定对某个任务启用 `planning-with-files`（多步骤/多轮工具调用/排障/调研）时，必须遵守：

### 1) 任务文件必须存在

在 `projects/<slug>/tasks/<task_id>/` 下创建：

- `task_plan.md`
- `findings.md`
- `progress.md`

模板来源：`skills/agency-dev-team/templates/{task_plan,findings,progress}.md`

### 2) 执行前必读

每次开始执行/做关键决策前：先读 `task_plan.md`（避免目标漂移）。

### 3) 执行中记录

- 外部资料/长摘录/不可信内容只写 `findings.md`
- 失败与尝试必须写 `progress.md`（避免重复踩坑）

### 4) 结束前回写（强制闭环）

任务阶段性完成/停止前必须：

- 更新 `progress.md`（本次做了什么、结果、结论、验证）
- 并把可执行摘要回写到项目 L1 文件：
  - 决策 → `DECISIONS.md`
  - 推进/下一步 → `HANDOFF.md`
  - 状态/阻塞/Next → `SUMMARY.md`

> 规则：启用 planning-with-files 但未维护 3 文件或未回写 L1，视为不合格输出。

## 工程门禁（强制：先读对应 skill 再执行）

以下场景属于“硬约束”，任何角色开始执行前必须先阅读对应 skill（以本 workspace 为准）：

- 代码评审 / PR review / diff 审查 → `skills/code-review/SKILL.md`

### 评审双门禁（强制顺序）

当进入“评审/合入/发布前检查”阶段时，必须按以下顺序执行：

1) 规格符合性评审（先对齐 spec/计划/现行约定）→ `skills/spec-compliance-review/SKILL.md`
2) 代码质量评审（再看质量/安全/性能/可维护性）→ `skills/code-review/SKILL.md`

> 规则：如果第 1 步 FAIL，则禁止进入第 2 步，必须先修正并更新项目事实源。
- 交付验收 / 回归 / 测试策略与用例设计 → `skills/testing/SKILL.md`
- TypeScript 大改 / 新 TS 模块 / 类型设计与边界 → `skills/typescript/SKILL.md`

补充建议（按需启用的工程子技能）：

- 写 README/交接/排障文档 → `skills/docs-writing/SKILL.md`
- 本地一键启动/环境变量/compose → `skills/devops-local-env/SKILL.md`
- 前后端并行开发前先定接口合同 → `skills/api-contract/SKILL.md`
- 线上/启动故障需要 runbook 化 → `skills/troubleshooting-runbook/SKILL.md`
- 日志/可观测性建设 → `skills/observability-logging/SKILL.md`
- 新需求/bug 分诊进 backlog → `skills/issue-triage/SKILL.md`

> 规则：如果没有先读 skill，输出一律视为不合格，Dev Lead 必须要求重做。

## 工程（Build）

- UI 组件/前端实现/性能：`engineering-frontend-developer.md`
- 系统架构/API/数据模型：`engineering-backend-architect.md`（或本团队改写版 `backend_web.md`）
- DevOps/CI/CD/部署：`engineering-devops-automator.md`
- PR 评审：`engineering-code-reviewer.md`
- 文档/README/API 文档：`engineering-technical-writer.md`
- 安全评审/威胁建模：`engineering-security-engineer.md`
- 可靠性/SLO/可观测性：`engineering-sre.md`

## 测试（Test）

- API 测试设计/用例：`testing-api-tester.md`
- 性能基准/压测与指标：`testing-performance-benchmarker.md`
- 泛 QA 清单：本团队 `qa.md`

## 产品（Product）

- 需求澄清/路线图/PRD：`product-manager.md`
- Sprint 排期与优先级：`product-sprint-prioritizer.md`

## 项目管理（PM）

- 项目推进/风险/节奏控制：`project-management-project-shepherd.md`

## 总分诊与计划（Chief of Staff）

- 需求/任务/问题过载，需要统一分诊与排队：`chief-of-staff.md`
- 需要把输入收敛为 Now/Next/Later 队列，并驱动分派与跟进：`chief-of-staff.md`

## 技术支持（Support）

- 故障/报错/无法运行/线上异常分诊：`support-triage.md`

### 什么时候必须引入 Project Shepherd（PM 总控）

满足任一条件时，Dev Lead 应显式指派 `project-management-project-shepherd.md` 作为“PM 总控”子角色协助：

- 子任务数 ≥ 3（跨前端/后端/QA/DevOps）且存在依赖关系
- 需要明确里程碑/交付日期/外部依赖（例如第三方接口、审批、上线窗口）
- 需求不稳定或范围可能变更，需要变更控制与节奏管理
- 项目出现 Yellow/Red 风险（延期、质量风险、阻塞）需要恢复计划

#### Project Shepherd 交付物约定（最小模板）

PM 总控输出必须包含：

- Overall Status：Green/Yellow/Red + 理由
- Milestones：本周/下周里程碑与日期（或相对时间）
- Dependencies：依赖与责任人
- Risks：Top 3 风险 + 缓解措施
- Decisions Needed：需要人类/Dev Lead 拍板的决策与推荐选项
- Next：接下来 3-7 条可执行 TODO（可分配到角色）

## 设计（Design）

- 视觉/组件规范：`design-ui-designer.md`

## 增长与运营（Operate/Growth）

- 内容生产：`marketing-content-creator.md`
- SEO：`marketing-seo-specialist.md`
- 社媒策略：`marketing-social-media-strategist.md`
- 增长实验：`marketing-growth-hacker.md`
- 数据与复盘：`support-analytics-reporter.md`
