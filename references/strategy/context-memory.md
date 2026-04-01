# Context & Memory Strategy（借鉴 OpenViking：分层、落盘、可追溯）

> 目标：在不引入 OpenViking 服务的情况下，借鉴其核心策略，让 OpenClaw 的上下文更“可控、可检索、可迭代”。

## 核心原则

1) **Filesystem as Brain**：上下文的事实源在文件系统里，不在聊天里。
2) **Tiered Loading**：把上下文分为 L0/L1/L2，按需加载，减少 token 噪音。
3) **Observable Retrieval**：每次关键结论都可追溯到文件路径（落盘 + 引用）。
4) **Write Once, Reuse Many**：重复流程/排障/评审清单要沉淀为 templates 或 skills。

---

## L0/L1/L2 分层定义（我们在 OpenClaw 的映射）

### L0（入口/导航/身份）——“先看这个，决定要不要深入”

- `BOOT.md`：启动必读顺序与硬约束
- `SOUL.md`：角色定位与强制流程（主控规范）
- `START_HERE.md`：使用说明/速查
- `projects/_index.md`：项目索引

### L1（项目工作记忆/可执行摘要）——“当前推进所需的最小上下文”

- `projects/<slug>/SUMMARY.md`：
  - TL;DR
  - 当前里程碑/关键路径
  - Top 风险与阻塞
  - Decisions Needed
  - 本周/下一步 TODO
- `projects/<slug>/PROJECT.md`：目标/范围/里程碑/约束
- `projects/<slug>/DECISIONS.md`：关键决策与取舍（Why）
- `projects/<slug>/HANDOFF.md`：当前进度/下一步/如何验证

### L2（原始材料/细节）——“需要时再打开”

- `docs/COMMANDS.md`、`docs/TROUBLESHOOTING.md`
- `references/**`（外部项目/资料，只读）
- 长日志、完整讨论记录、外部链接摘录

---

## 检索/加载决策树（简版）

1) **用户提到项目 `<slug>`？**
   - 是：优先读 L1（SUMMARY → PROJECT/DECISIONS/HANDOFF）
   - 否：只读 L0（SOUL/START_HERE/_index），必要时询问 slug

2) **任务类型是什么？**
   - 评审 → 先读 `skills/code-review/SKILL.md`
   - 测试/验收 → 先读 `skills/testing/SKILL.md`
   - 排障 → 先读 `skills/troubleshooting-runbook/SKILL.md`，并确保更新 `docs/TROUBLESHOOTING.md`

3) **是否需要深入到 L2？**（满足任一才深入）
   - 需要复现/定位错误（必须看日志/命令输出）
   - 需要引用外部项目实现细节（references）
   - L1 信息不够支撑决策

---

## 什么时候触发“整理/摘要/落盘”（触发器）

- 出现关键决策（技术选型、接口合同、目录结构）→ 写入 `DECISIONS.md`，并在 `SUMMARY.md` 更新“现行约定”
- 完成阶段性里程碑（M1/M2）→ 更新 `HANDOFF.md` + `SUMMARY.md`
- 对话/任务变长（信息开始散）→ 把“现阶段 TL;DR + Next”写入 `SUMMARY.md`
- 重复出现同类问题（排障/支持）→ 更新 `docs/TROUBLESHOOTING.md`（runbook 化）
- 新增可复用流程 → 升级为 `skills/<name>/SKILL.md` 或 `templates/*.md`

---

## 跳过规则（避免噪音）

- 不把长日志直接写入 L1；只在 L2 存链接/摘要。
- 不把 references 当事实源；只用作参考，并把最终结论落盘到 projects 或 skills。
- 不为“单次、不可复用”细节创建 skill；先写到项目 HANDOFF/NOTES。
