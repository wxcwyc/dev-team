# spec-compliance-review

规格符合性评审（Spec Compliance Review）：在做代码质量评审之前，先确认“实现是否符合已批准的规格/计划/当前项目约定”。

## 适用场景

- 完成一个里程碑/任务包后（准备进入 code review）
- 合并/发布前
- 发现实现偏离、需求漂移、反复返工时

## 必读输入（最小集合）

- `projects/<slug>/SUMMARY.md`
- `projects/<slug>/PROJECT.md`
- `projects/<slug>/DECISIONS.md`
- `projects/<slug>/HANDOFF.md`
- 本次变更说明（目标、涉及模块/文件）

## 输出（必须包含）

1) Verdict：PASS / WARN / FAIL
2) Coverage：本次实现覆盖了哪些需求点/验收标准
3) Deviations：偏离规格/计划/现行约定的点（含“是否可接受”建议）
4) Gaps：缺失点（未实现/未验证/未落盘）
5) Risks：引入的新风险（兼容性/安全/性能/维护）
6) Next：按优先级列出 3-7 条修正步骤
7) 落盘建议：需要更新哪些文件（DECISIONS/HANDOFF/SUMMARY）

## 评审方法（简版）

- 先以 `SUMMARY.md` 为准：当前状态、Next、约定是什么
- 再对照 PROJECT 的范围与验收
- 再核对 DECISIONS 的“现行约定”（框架/目录/API/错误结构）
- 最后看 HANDOFF：本轮是否按计划推进、是否补了验证方式

## 输出模板

```text
# Spec Compliance Review — <slug> — <date>

## Verdict
PASS/WARN/FAIL — <one line reason>

## Coverage
- ...

## Deviations
- ... (Accept?/Why)

## Gaps
- ...

## Risks
- ...

## Next (Prioritized)
1) ...

## Writeback (落盘)
- SUMMARY:
- DECISIONS:
- HANDOFF:
```

## 关联门禁

- 通过/完成本评审后，才进入：`skills/code-review/SKILL.md`
