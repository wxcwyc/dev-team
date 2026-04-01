# agency-dev-team

一套“多代理开发团队”模板：主会话做 Tech Lead/PM 统筹，子代理按职能（后端/前端/QA/DevOps/文档）分工协作。

> 目标：不把助手绑死到某个仓库；用**统一的文件结构 + 交付物约定 + 调度规则**，让任意项目都能快速启动。

## 适用场景

- 你同时推进多个软件项目，需要统一规范与复用角色。
- 你希望把任务拆分给不同“专职子代理”，主助手负责收敛决策。
- 你需要一套可复制的工程化输出：计划、patch、测试计划、发布清单。

## 不做什么（边界）

- 不提供任何破限/越狱/绕过平台安全限制的方法。
- 不协助违法、有害、侵犯隐私的操作。

## 目录结构（workspace 内建议）

本 skill 在 workspace 下生成/使用以下结构：

```
skills/agency-dev-team/
  SKILL.md
  souls/
    dev_lead.md
    backend_web.md
    qa.md
  templates/
    project_brief.md
    handoff.md
    decision_log.md
references/
  agency-agents/roles/   # （可选）外部角色库镜像，用于按需摘取
```

项目级的共享“事实源”建议放在：

```
projects/<project_slug>/
  PROJECT.md
  DECISIONS.md
  HANDOFF.md
  backlog.md
  notes/
```

## 角色与职责

### 1) 主会话：开发总监/Tech Lead（Dev Lead）

- 复述需求、澄清约束
- 拆解 2-5 个子任务
- 为每个子任务选择合适的子代理
- 汇总子代理结果并给出最终决策、TODO、风险

推荐工具/技能：
- coding-agent（大规模代码任务/重构/长任务）
- skill-creator（生成/维护 skill & SOUL 模板）
- healthcheck（部署前后检查/安全基线）

### 2) 子代理：Web 后端（Backend Web）

- 读取指定仓库/模块
- 设计接口、数据模型、错误处理
- 输出 patch/diff + 测试建议

### 3) 子代理：测试/QA

- 基于需求与代码现状给出测试策略
- 产出可执行测试用例/测试清单
- 发现风险与回归点

## 调度规则（建议写进主会话 SOUL）

收到需求时：

1. 一句话复述需求
2. 判断：是否是新项目？是否需要先建 `projects/<slug>/PROJECT.md`？
3. 拆解为子任务（按职能）
4. 给每个子任务明确交付物：
   - 设计：在 `DECISIONS.md` 记录决策与取舍
   - 实现：patch/diff + 验收标准
   - QA：测试清单 + 复现步骤 + 风险等级
5. 汇总为“可执行下一步”

## 快速启动（人类操作）

1) 选择/创建项目目录：`projects/<slug>/`

2) 填写 `PROJECT.md`（用 templates/project_brief.md）

3) 在主会话发：

- “按 agency-dev-team 方式启动项目 <slug>，先输出任务拆解与分工。”

## 精选 roster（开发 → 上线 → 运营 的最小可用集合）

> 这些角色文件位于：`skills/agency-dev-team/souls/`。
> 
> 完整的外部角色库（不参与日常调度）位于：`references/agency-agents/roles/`。

### 工程（Build）

- `engineering-frontend-developer.md` — 前端实现/性能
- `backend_web.md` / `engineering-backend-architect.md` — 后端架构/API/数据模型
- `engineering-devops-automator.md` — CI/CD、部署、自动化
- `engineering-code-reviewer.md` — 代码评审
- `engineering-technical-writer.md` — 技术文档
- `engineering-security-engineer.md` — 安全设计与审计
- `engineering-sre.md` — 可靠性/可观测性/SLO

### 测试（Test）

- `qa.md` — 通用 QA 清单
- `testing-api-tester.md` — API 测试策略/用例
- `testing-performance-benchmarker.md` — 性能基准/压测

### 产品与项目管理（Product/PM）

- `product-manager.md` — 需求澄清、PRD、路线图
- `product-sprint-prioritizer.md` — Sprint 优先级与拆分
- `project-management-project-shepherd.md` — 项目推进、风险与节奏

### 设计（Design）

- `design-ui-designer.md` — UI 设计与组件规范

### 增长与运营（Operate/Growth）

- `marketing-content-creator.md` — 内容产出
- `marketing-seo-specialist.md` — SEO
- `marketing-social-media-strategist.md` — 社媒策略
- `marketing-growth-hacker.md` — 增长实验
- `support-analytics-reporter.md` — 数据与复盘

## 使用范式（建议）

1) **选定项目**：创建 `projects/<slug>/` 并填写 PROJECT/DECISIONS/HANDOFF（模板见 `skills/agency-dev-team/templates/`）

2) **主会话发起**：

- “按 agency-dev-team 启动项目 `<slug>`：读取 `projects/<slug>/PROJECT.md`，按 `skills/agency-dev-team/ROUTING.md` 拆 2-5 个子任务并分工。”

3) **子代理交付物约定**：

- 任何方案类输出必须包含：交付物 + 验收标准 + 风险
- 任何实现类输出必须包含：patch/diff（或精确替换片段）+ 运行/验证步骤
- 关键决策必须被主会话写入 `DECISIONS.md`
- 阶段性推进必须更新 `HANDOFF.md`

## 外部角色库（agency-agents）

如果你本地已 clone `msitarzewski/agency-agents`，建议把“全量角色”放在 workspace 的参考库路径：

- `references/agency-agents/roles/`

然后只把你真正需要的 10-20 个角色摘取/改写成 `skills/agency-dev-team/souls/*.md`，避免主团队 skill 变得臃肿、难以调度。
