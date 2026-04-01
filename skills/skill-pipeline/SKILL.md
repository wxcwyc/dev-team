---
name: skill-pipeline
description: |
  Dev-team 轻量编排器：在任何开发/排障/评审任务开始前，先做任务分级（Trivial/Small/Medium/Large/Long-running/Incident），再选择需要启用的门禁技能与工件（SUMMARY / planning-with-files / review gates）。

  Use when: 你准备开始任何非纯聊天的“做事”请求（开发/排障/评审/上线）。
  NOT for: 纯闲聊、纯信息查询（无执行）。
---

# Skill: skill-pipeline（dev-team 轻量总编排）

> 目标：把流程“恰到好处”地加在该加的地方：小事不拖，大事不漏。

## 输入
- 用户请求（要做什么）
- 是否选定项目 `<slug>`
- 是否涉及：鉴权/支付/迁移/并发/线上故障（高风险信号）

## 输出
- Task Class（分级）
- 必须启用的门禁（skills + 工件）
- 下一步行动清单（1-5 条）

## Step 1 — 任务分级（Task Class）

按下面信号快速判断（不确定时升一级）：

- **Trivial**：拼写/文案/小改名/单行配置；无风险
- **Small**：单点修复；单文件；<10 行逻辑变更；无高风险域
- **Medium**：2-5 文件；功能点明确；可在一次会话完成
- **Large**：跨模块/架构调整/不熟悉区域/高风险域（鉴权、并发、迁移、支付、风控）
- **Long-running**：需要多会话、多阶段推进，或信息量大导致上下文压力明显
- **Incident**：启动失败/线上故障/500/超时/不可用

## Step 2 — 选择门禁与工件（Depth Routing）

| Task Class | 必须启用 | 必须产物 |
|---|---|---|
| Trivial | （可选）code-review | 若影响项目：HANDOFF Done/Next |
| Small | Intent Frame + Mini S&H | HANDOFF Next（3 行计划即可） |
| Medium | Spec→Plan→Execute + Mini S&H + 评审双门禁 | PROJECT/DECISIONS/HANDOFF 更新 |
| Large | planning-with-files + 评审双门禁 | tasks/<task_id>/{task_plan,findings,progress}.md + SUMMARY |
| Long-running | planning-with-files + SUMMARY 门禁（每次先读） | SUMMARY 持续更新 + HANDOFF Next |
| Incident | support-triage → systematic-debugging → runbook | docs/TROUBLESHOOTING.md 更新 |

说明：
- **Intent Frame**：使用 `skills/agency-dev-team/templates/intent_frame.md`
- **评审双门禁**：先 `spec-compliance-review` 再 `code-review`

## Step 3 — 执行前 0-3 个澄清问题
只问会改变方案的关键点；如果已足够明确，直接进入 Intent Frame。

## Step 4 — 输出“路由决策”
用下面格式输出，便于审阅：

```
[skill-pipeline]
Task Class: <...>
Gates: <...>
Artifacts: <...>
Next: 1) ... 2) ...
```

## Anti-patterns（禁止）
- 不要把 Trivial/Small 任务升级成大流程（会拖慢团队）
- 不要绕过 SUMMARY/Intent Frame/评审门禁（会导致返工与质量问题）
- 不要在未落盘的情况下进入实现（Spec/Plan 缺失时必须先补齐）
