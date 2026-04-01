# issue-triage

需求/缺陷分诊技能：把“一个问题”变成可执行的任务单与优先级。

## 适用场景
- 用户反馈/bug
- 新需求进入 backlog
- 线上 incident 后续

## 输出（必须包含）
- 类型：Bug / Feature / Chore / Question
- 优先级：P0-P3（含理由）
- 复现步骤（Bug）或验收标准（Feature）
- 影响范围与风险
- Owner 建议（按 ROUTING 路由到 Frontend/Backend/DevOps/QA）
- 下一步（3-7 条）

## 模板（最小）

```text
Title:
Type:
Priority:
Context:
Repro / Acceptance:
Impact/Risk:
Owner role:
Next:
```

## 参考（武器库）
- `references/lobehub/.agents/skills/`（技能拆分思路）
- `references/everything-claude-code/agents/chief-of-staff.md`（分诊队列思想）
