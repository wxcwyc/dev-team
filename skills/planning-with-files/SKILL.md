# planning-with-files

任务级“写计划”技能：借鉴 planning-with-files 的 3-file pattern，把长任务的计划/发现/进度外置到文件，防止目标漂移与重复踩坑。

## 适用场景（建议用）
- 多步骤任务（≥3 步）
- 需要多次工具调用/多轮调试
- 需要调研/阅读大量资料
- 多代理并行执行（需要共享计划与进度）

不建议用：
- 单文件小改
- 简单问答

## 核心结构（3-file pattern）

在 `projects/<slug>/tasks/<task_id>/` 下创建：

- `task_plan.md`：目标、分阶段计划、验收标准、状态（checkbox）
- `findings.md`：调研发现、链接/引用、关键摘录（不可信内容优先放这里）
- `progress.md`：实验记录、命令输出摘要、错误与修复尝试（错误持久化）

## 与分层记忆的关系（L0/L1/L2）

- 项目级 L1：`projects/<slug>/SUMMARY.md`（只保留可执行摘要）
- 任务级 3 文件属于 L2（证据链/过程），但会反哺 L1：
  - 关键决策 → `DECISIONS.md`
  - 阶段推进/下一步 → `HANDOFF.md`
  - 当前状态/阻塞 → `SUMMARY.md`

## 强制规则

1) **Create Plan First**：未创建 `task_plan.md` 不得进入实现。
2) **Log ALL Errors**：任何失败必须记在 `progress.md`（含尝试与结果）。
3) **Never Repeat Failures**：重复失败前先读 `progress.md`，换策略。
4) **Findings 不污染计划**：外部搜索/长摘录只写 `findings.md`，不要写进 `task_plan.md`。

## 输出模板

- 使用：
  - `skills/agency-dev-team/templates/task_plan.md`
  - `skills/agency-dev-team/templates/findings.md`
  - `skills/agency-dev-team/templates/progress.md`

## 典型触发语

- “这个任务步骤多，用 planning-with-files 建一个 task_id=<x> 的三文件计划。”
- “把排障过程写进 progress.md，并把最终结论回写到 HANDOFF/SUMMARY。”
