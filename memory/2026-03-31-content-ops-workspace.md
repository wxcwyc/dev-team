# 2026-03-31 — 新增 workspace：content-ops（通用内容工作流水线）

## 用户目标
建立一套可执行的通用 skill/工作流，让 AI 能覆盖：市场分析、运营策划、热点追踪、短视频脚本+分镜、写作等。
要求：先生成 Markdown 规格/计划，再在此基础上产出可直接发布成品（脚本、标题、镜头表、贴文、日历）。

## 交付（已落盘）
新增 workspace：`/Users/gawin/.openclaw/workspace-content-ops/`

### 核心文件
- `BOOT.md`：启动门禁（先分级→Intent→Spec→Deliverable→QA→落盘）
- `SOUL.md`：Content Ops Lead 人设与事实源
- `AGENTS.md`：目录规范与工作原则
- `MEMORY.md`：长期规则摘要
- `START_HERE.md`：最短用法与标准启动口令
- `projects/_index.md`

### 核心 skill
- `skills/content-ops-pipeline/SKILL.md`
  - Task Class 分级（Trivial/Small/Medium/Large/Long-running）
  - Intent Frame（强制确认）
  - Spec 模板路由（市场分析/运营策划/热点/短视频/写作）
  - Deliverable（可发布成品）
  - 发布前 QA（事实核查/合规/风格/格式/CTA）
  - DECISIONS/HANDOFF 落盘闭环

### templates
- `templates/intent_frame.md`
- `templates/spec_market_analysis.md`
- `templates/spec_ops_plan.md`
- `templates/spec_trend_radar.md`
- `templates/spec_video_storyboard.md`
- `templates/spec_writing.md`
- `templates/qa_publish_checklist.md`
- `templates/project_brief.md`（PROJECT）
- `templates/decision_log.md`（DECISIONS）
- `templates/handoff.md`（HANDOFF）
- `templates/project_summary.md`（SUMMARY）

## 使用口令（建议）
“按 content-ops-pipeline 启动项目 <slug>：先读 SUMMARY，再按 SKILL 分级与路由；输出 Intent Frame 并确认；先产出 Markdown spec，再生成可发布成品；发布前跑 QA 清单；关键决策写入 DECISIONS，推进更新 HANDOFF。”
