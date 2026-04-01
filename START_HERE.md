# workspace-dev-team — 使用说明（给人 & 给代理）

本目录是 OpenClaw 的“多代理开发团队（Dev Lead）”工作区：

- **唯一事实源**：项目状态与关键决策必须落在这里（`projects/<slug>/...`）。
- **团队技能副本**：本 workspace 内包含一份可编辑的 `skills/agency-dev-team/`，用于固化路由/角色与模板。

> 目标：任何人/任何代理进入这个 workspace，都能快速知道：从哪读、怎么启动项目、遇到什么情况用哪个角色/skill。

---

## 0. 必读（每次开工）

按顺序读取：

1) `BOOT.md`
2) `SOUL.md`
3) `MEMORY.md`
4) `projects/_index.md`

若已选定项目 `<slug>`，再读：

- `projects/<slug>/PROJECT.md`
- `projects/<slug>/DECISIONS.md`
- `projects/<slug>/HANDOFF.md`

---

## 1. 项目事实源结构（必须遵守）

每个项目都在：

```
projects/<slug>/
  SUMMARY.md    # L1 可执行摘要（先读这个再深入）
  PROJECT.md    # 目标/范围/里程碑/约束
  DECISIONS.md  # 关键决策与取舍（为什么这么选）
  HANDOFF.md    # 当前进度/下一步/如何验证
```

`projects/_index.md` 是项目目录索引入口。

---

## 2. 角色（souls）与调度规则（ROUTING）

调度规则：

- `skills/agency-dev-team/ROUTING.md`

角色库：

- `skills/agency-dev-team/souls/*.md`

### 常用角色速查（什么时候用谁）

- **Dev Lead**（主会话）
  - 负责：澄清 → 拆分 → 指派 → 评审 → 收敛 → 落盘
  - 规范：`skills/agency-dev-team/souls/dev_lead.md`

- **Chief of Staff（参谋长/总分诊）**
  - 用于：任务/想法/问题太多，需要统一排队、分诊、驱动分派与跟进
  - 输出：Decisions / Blockers / Now / Next / Later
  - 文件：`skills/agency-dev-team/souls/chief-of-staff.md`

- **Project Shepherd（项目经理/推进）**
  - 用于：跨职能依赖、里程碑/节奏、风险与状态报告
  - 文件：`skills/agency-dev-team/souls/project-management-project-shepherd.md`

- **Backend Architect / Backend Web**
  - 用于：API、数据模型、后端实现方案与 patch
  - 文件：`skills/agency-dev-team/souls/engineering-backend-architect.md`（或 `backend_web.md`）

- **Frontend Developer**
  - 用于：React/Vue 等前端实现、性能、组件
  - 文件：`skills/agency-dev-team/souls/engineering-frontend-developer.md`

- **QA / API Tester**
  - 用于：测试策略、用例、回归清单
  - 文件：`skills/agency-dev-team/souls/qa.md`、`skills/agency-dev-team/souls/testing-api-tester.md`

- **DevOps Automator**
  - 用于：docker/CI/CD/部署脚本/环境配置
  - 文件：`skills/agency-dev-team/souls/engineering-devops-automator.md`

- **Support Triage（技术支持分诊）**
  - 用于：启动失败、报错、线上异常的复现/归因/分派/验证 + runbook 草案
  - 文件：`skills/agency-dev-team/souls/support-triage.md`

---

## 3. skills 与工具（什么时候用哪个）

> 说明：这里的“skill”是 OpenClaw 的工作规范/模板集合；实际写代码时通常需要编码代理。

### 3.1 agency-dev-team（团队流程/角色/模板）

- 位置：`skills/agency-dev-team/`
- 用于：统一拆分、分工、交付物约定、模板、路由

典型触发语：
- “按 agency-dev-team 启动项目 <slug>”
- “按 ROUTING 拆 2-5 个子任务并分工”

### 3.2 project-bootstrapper（项目初始化）

- 位置：`skills/project-bootstrapper/`
- 用于：快速生成 `projects/<slug>` 三件套 + 更新索引；（可扩展）生成 repo 骨架

典型触发语：
- “用 project-bootstrapper 初始化项目 <slug>，技术栈 React/Node/Mongo，mono-repo”

### 3.3 coding-agent（并行编码/重构/长任务）

- 用于：当需要大量代码实现时，委托 Codex/Claude Code 等编码代理执行
- 适用：新功能、重构、跨文件修改、PR 级改动

### 3.4 healthcheck / node-connect / skill-creator

- `healthcheck`：OpenClaw 部署安全/健康检查（SSH/防火墙/更新策略等）
- `node-connect`：OpenClaw 设备/节点连接与配对故障排查
- `skill-creator`：创建/整理/审计 skill（当你要把流程固化成可复用能力时）

### 3.6 context-strategy（上下文/记忆分层策略）

- 位置：`skills/context-strategy/`
- 用于：把上下文分为 L0/L1/L2，按需读取/按规落盘，避免噪音与遗忘

L0/L1/L2 写入位置（简表）：
- **L0（入口/导航）**：`BOOT.md` / `SOUL.md` / `START_HERE.md` / `projects/_index.md`
- **L1（项目可执行记忆）**：`projects/<slug>/SUMMARY.md` + PROJECT/DECISIONS/HANDOFF
- **L2（细节/证据）**：`docs/` + `references/` + 日志/长输出

### 3.7 planning-with-files（任务级写计划：3-file pattern）

- 位置：`skills/planning-with-files/`
- 用于：为长任务/排障/调研建立任务级 3 文件（task_plan/findings/progress），减少目标漂移与重复踩坑
- 任务文件建议路径：`projects/<slug>/tasks/<task_id>/task_plan.md | findings.md | progress.md`

### 3.5 工程子技能（从 lobehub 提炼的可复用技能）

- `skills/code-review/`：代码评审清单与风险分级（参考 lobehub / everything-claude-code 提炼）
- `skills/testing/`：最小可行测试策略与用例模板
- `skills/typescript/`：TS 类型边界与工程规范

评审与排障增强：

- `skills/spec-compliance-review/`：规格符合性评审（先对齐 spec/计划/约定，再做 code-review）
- `skills/systematic-debugging/`：系统化排障（证据链 + 最小实验 + 验证/回归 + 强制写 runbook）

扩展（通用工程能力）：

- `skills/docs-writing/`：README/交接/排障文档写作规范
- `skills/devops-local-env/`：本地环境、一键启动与 env/compose 规范
- `skills/api-contract/`：API 合同（字段/路由/错误码/示例）
- `skills/troubleshooting-runbook/`：排障 runbook 化与沉淀规范
- `skills/observability-logging/`：日志规范与最小可观测性
- `skills/issue-triage/`：需求/缺陷分诊与优先级模板

---

## 4. 标准启动范式（给人类/代理照抄）

### 4.1 新项目

1) 创建事实源：
   - `projects/<slug>/PROJECT.md | DECISIONS.md | HANDOFF.md`
2) 在主会话发：
   - “按 agency-dev-team 启动项目 <slug>：读取 PROJECT，按 ROUTING 拆 2-5 个子任务并分工。”
3) 决策落盘到 `DECISIONS.md`，阶段进展落盘到 `HANDOFF.md`

### 4.2 需要计划/排队

- “用 Chief-of-Staff 给 <slug> 输出 Now/Next/Later，并列出 Decisions Needed 和 Blockers。”

### 4.3 出现报错/无法运行/线上异常

- “用 Support Triage 对 <slug> 做分诊：给复现步骤、初步定位、owner 分派、验证步骤、runbook 草案。”

> 技术支持补充：
> - 常用命令速查：`docs/COMMANDS.md`
> - 常见问题/排障手册：`docs/TROUBLESHOOTING.md`
> - 约定：Support Triage 处理完问题后，必须推动把 runbook 条目落盘更新到 `docs/TROUBLESHOOTING.md`（或项目内 runbooks）。

---

## 5. 写作/交付物硬约束（保证可验收）

- 每个子任务必须写清：**Deliverables + Acceptance + Risks/Deps**
- 关键决策必须落到：`DECISIONS.md`
- 阶段推进必须更新：`HANDOFF.md`

推荐使用的模板（位于 `skills/agency-dev-team/templates/`）：

- `status_report.md`：PM 状态报告模板（Project Shepherd）
- `support_runbook.md`：支持/排障条目模板（Support Triage）
- `release_checklist.md`：发布/交付检查清单（Release Captain / Dev Lead）
- `api_test_minset.md`：HTTP API 最小测试集（集成测试/验收）

---

## 6. 参考库（只读）

本 workspace 挂载了一个只读参考库（不参与事实源，不要在其中落盘项目状态）：

- `references/everything-claude-code/` → `/Users/gawin/my-project/everything-claude-code`

用途：借鉴其角色写法、命令速查、排障手册、评估清单等。

---

## 7. 方法论路由器（自动切换策略）

当出现“阶段变化/阻塞/失败/准备评审与发布”等信号时，按路由器策略自动切换到对应 skill 与落盘动作：

- `references/strategy/methodology-router.md`

（它整合了：Spec→Plan→Execute→Review→Release 的门禁，以及 Support→Debug→Runbook 的升级路径。）
