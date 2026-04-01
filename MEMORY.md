# MEMORY.md（长期记忆 / 开发团队主会话）

## 目标
在 OpenClaw 中运行一套可复用的“多代理开发团队”（agency-dev-team）：
- 主会话 = Dev Lead（拆任务、调度、收敛决策）
- 子代理 = 按职能（后端/前端/QA/DevOps/文档等）
- 持久记忆以 workspace 文件为事实源：PROJECT/DECISIONS/HANDOFF/INDEX

## 主会话工作方式（Dev Lead 规则）
1) 一句话复述需求
2) 只问影响方案的 0-3 个澄清问题
3) 维护项目事实源文件：
   - projects/<slug>/PROJECT.md
   - projects/<slug>/DECISIONS.md
   - projects/<slug>/HANDOFF.md
4) 拆分 2-5 个子任务并指定交付物与验收标准
5) 必要时拉起子代理（后端/QA/DevOps/文档）产出分工交付
6) 汇总为可执行 TODO 列表 + 风险/依赖

## 工具/模板位置
- 团队模板：skills/agency-dev-team/
- Dev Lead SOUL：skills/agency-dev-team/souls/dev_lead.md
- Backend SOUL：skills/agency-dev-team/souls/backend_web.md
- QA SOUL：skills/agency-dev-team/souls/qa.md
- 项目模板：skills/agency-dev-team/templates/

## 偏好
- 输出偏工程化：步骤、验收标准、回滚/测试策略
- 关键结论必须落盘到项目文件，避免上下文变长丢失

## 2026-03-31 关键约定：agency-dev-team 事实源路径
- 唯一事实源：本 workspace（当前目录）
  - 启动门禁：先读 `BOOT.md`
  - 团队规范：`skills/agency-dev-team/`（ROUTING/templates/souls）
- 主 workspace 对齐：主 workspace 的 `skills/agency-dev-team` 使用软链接指向本 workspace 的增强版（迁移/多机时需要重建软链接；备份目录名包含时间戳）。
- 术语：角色(roster)来自 `skills/agency-dev-team/souls/*.md`；其他 `skills/*` 多为流程/方法论技能，通常由 ROUTING 的工程门禁按场景显式要求使用。
- 详见：`memory/2026-03-31-agency-dev-team-paths.md`

## 2026-03-31 增强：dev-team 轻量 pipeline（P0+P1）
- 目标：借鉴 pskoett-ai-skills 的 pipeline/intent framing/post-completion quality pass 思想，增强但不过度。
- 已落盘：
  - `BOOT.md` 增加 Task Class 分级与流程深度门禁
  - `skills/agency-dev-team/ROUTING.md` 增加 Intent Frame 门禁与完成后 Mini Simplify & Harden 门禁（再进入 spec-compliance-review → code-review）
  - 新增 `skills/agency-dev-team/templates/intent_frame.md`
  - 新增轻量编排器：`skills/skill-pipeline/SKILL.md`
- 详见：`memory/2026-03-31-skill-pipeline-integration.md`

## 2026-03-31 新增：content-ops workspace（通用内容工作流水线）
- 目标：覆盖市场分析/运营策划/热点追踪/短视频脚本+分镜/写作；先 Markdown spec，再产出可发布成品；发布前 QA；落盘决策与交接。
- 新 workspace：`/Users/gawin/.openclaw/workspace-content-ops/`
- 核心 skill：`skills/content-ops-pipeline/SKILL.md`
- 配套模板：intent/spec/QA/PROJECT/DECISIONS/HANDOFF/SUMMARY
- 详见：`memory/2026-03-31-content-ops-workspace.md`
