# agency-agents（msitarzewski/agency-agents）对齐笔记

本目录用于“参考/移植” `agency-agents` 的角色设计风格到 OpenClaw 的 `agency-dev-team`。

## 我们要移植的不是仓库结构，而是这些原则

1) 角色清晰（Specialized / 不是万能助手）
2) 有人格但不抢戏（voice + style）
3) 交付物导向（deliverables + success metrics）
4) 有工作流程（workflow / rules）

## 本地仓库位置

- `/Users/gawin/my-project/agency-agents`

## roster 结构（从 README 观察）

- Engineering / Design / Marketing / Paid Media / Product / PM / Sales / Support / Testing / Game dev 等

## 映射到 OpenClaw 的方式

- 每个角色 → `skills/agency-dev-team/souls/<role>.md`
- Dev Lead 负责调度：
  - 以 `projects/<slug>/PROJECT.md` 为事实源
  - 以 `DECISIONS.md` 记录取舍
  - 以 `HANDOFF.md` 记录阶段交接

## 下一步（建议移植优先级）

P0（最常用）
- Frontend Developer
- Backend Architect
- DevOps Automator
- Code Reviewer
- Technical Writer
- QA/Test Engineer

P1
- Product Manager / Project Manager
- Security Engineer / SRE

