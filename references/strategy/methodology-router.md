# Methodology Router（方法论路由器）— OpenClaw 多代理团队

> 目的：借鉴“自动路由/自动升级策略”的思想（如 superpowers / pua 一类项目的机制），但不引入其话术与平台绑定实现。
> 
> 结果：当出现特定信号（阶段/失败/阻塞/交付），主会话与子角色应自动切换到对应 skill 与落盘动作。

---

## 0) 默认前置（任何任务开始前）

- 若用户指定 `<slug>`：必须先读 `projects/<slug>/SUMMARY.md`（分层记忆门禁）
- 未指定 `<slug>`：只读 L0（`BOOT/SOUL/START_HERE/projects/_index`），并尽快确认项目

---

## 1) 阶段路由（Spec → Plan → Execute → Review → Release）

### 1.1 需求澄清/规格阶段（Spec）

触发信号：
- “想做/需要/实现一个…”
- 范围不清、约束不明、方案分歧

动作：
- Dev Lead：0-3 个澄清问题
- 落盘：更新 `PROJECT.md`（范围/里程碑）与 `DECISIONS.md`（关键取舍）
- 更新：`SUMMARY.md`（TL;DR + Decisions Needed）

### 1.2 计划阶段（Plan）

触发信号：
- 用户说“开始/启动/给计划/拆任务”
- 多人/多角色并行、存在依赖

动作：
- 先用 `Chief-of-Staff` 生成 Now/Next/Later + Blockers/Decisions Needed
- 若子任务 ≥3 且有依赖：引入 `Project Shepherd` 输出 PM Status（G/Y/R）
- 落盘：`HANDOFF.md`（Next）+ `SUMMARY.md`（Now/Next/Blockers）

### 1.3 执行阶段（Execute）

触发信号：
- 已明确任务包、owner、验收标准

动作：
- 按 ROUTING 指派工程角色
- 任何实现类任务必须带：Deliverables + Acceptance + Risks/Deps

### 1.4 评审阶段（Review）

触发信号：
- “做完了/准备合并/请 review/验收”

动作（硬顺序）：
1) `skills/spec-compliance-review/`（先对齐 spec/计划/现行约定）
2) `skills/code-review/`（再看质量/安全/性能/可维护性）
3) 如涉及验收/回归：`skills/testing/`

落盘：
- 偏离与修正：写入 `DECISIONS.md`/`HANDOFF.md`
- `SUMMARY.md` 更新当前状态（Green/Yellow/Red）与 Next

### 1.5 发布/交付阶段（Release）

触发信号：
- “上线/交付/demo 给别人跑/发版”

动作：
- 使用模板：`skills/agency-dev-team/templates/release_checklist.md`
- 落盘：`HANDOFF.md`（如何运行/验证/回滚）

---

## 2) 故障/阻塞升级路由（Support → Debug → Runbook）

### 2.1 技术支持分诊（Support Triage）

触发信号：
- “启动失败/报错/连不上/500/超时/接口不通”

动作：
- 使用：`skills/agency-dev-team/souls/support-triage.md`
- 强制：补 `docs/TROUBLESHOOTING.md`（新增或扩展条目）

### 2.2 系统化排障（Systematic Debugging）

触发信号（任一满足即升级）：
- Support Triage 后仍无法确定根因
- 同类问题重复出现
- 线上/核心流程受影响（S0/S1）

动作：
- 使用：`skills/systematic-debugging/`
- 强制：证据链 + 最小实验 + 验证/回归
- 强制：更新 `docs/TROUBLESHOOTING.md`

---

## 3) 记忆/上下文升级（避免噪音与遗忘）

触发信号（任一满足即更新 SUMMARY）：
- 关键决策出现
- 进入/完成里程碑
- 状态 Yellow/Red 或出现 Blocker
- 任务拆分 ≥3 且有依赖

动作：
- 更新：`projects/<slug>/SUMMARY.md`
- 同步：关键决策写 `DECISIONS.md`，推进写 `HANDOFF.md`

---

## 4) 何时去“武器库”（references/）

原则：只有当当前 `skills/` 中无对应能力或不足以解决问题时，才访问 `references/`。

推荐顺序：
1) 先查 `START_HERE.md` 的技能速查
2) 再查对应 `skills/<name>/SKILL.md`
3) 仍不足 → 查 `references/weaponry/*/INDEX.md`
4) 最后才直接翻外部仓库内容（`references/<repo>/...`）
