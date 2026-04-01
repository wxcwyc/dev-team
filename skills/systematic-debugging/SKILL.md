# systematic-debugging

系统化排障技能：把“猜问题”变成“证据链”。目标是快速定位根因，并用验证/回归闭环确保真的修好。

## 适用场景

- Support Triage 已收敛信息，但仍无法确定根因
- 线上间歇性故障、超时、5xx
- 复杂集成问题（前端/后端/DB/网络/配置）

## 强制规则

- 任何结论都必须有证据（日志/最小复现/实验结果）。
- 每轮最多 3 个假设；每个假设必须给出“如何证伪”的最小实验。
- 修复后必须提供验证步骤 + 回归点。
- 必须推动更新 `docs/TROUBLESHOOTING.md`（新增或扩展条目）。

## 四阶段流程（固定）

### Phase 1: Reproduce（复现）
- 明确最短复现步骤
- 固定环境与版本（记录关键信息）

### Phase 2: Hypothesize（提出假设）
- 输出最多 3 条假设，按概率排序
- 每条写：为什么可能、需要什么信号、如何证伪

### Phase 3: Experiment（最小实验）
- 每次只改变一个变量
- 记录实验结果（Pass/Fail + 观察到的信号）

### Phase 4: Fix & Verify（修复与验证）
- 给出修复方案（最小改动优先）
- 验证：复现用例通过 + 回归清单
- 沉淀 runbook（写入 docs/TROUBLESHOOTING）

## 输出模板（必须使用）

```text
# Systematic Debugging — <slug>

## Problem Statement
- Summary:
- Severity:
- Scope:

## Repro
- Steps:
- Environment:
- Signals (logs/metrics):

## Hypotheses (<=3)
1) Hypothesis:
   - Why:
   - Falsify test:

## Experiments
- Exp 1: <change>
  - Result:
  - Interpretation:

## Fix Proposal
- Fix:
- Verify:
- Regression:

## Writeback
- Update: docs/TROUBLESHOOTING.md (section: ...)
```

## 参考

- 技术支持分诊：`skills/agency-dev-team/souls/support-triage.md`
- runbook 模板：`skills/agency-dev-team/templates/support_runbook.md`
