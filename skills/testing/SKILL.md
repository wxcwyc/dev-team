# testing

测试技能：为项目提供最小可行的测试策略与可执行用例模板。

## 适用场景

- 新功能交付前
- bugfix 防回归
- 发布/交付 demo 前

## 输出（必须包含）

- 测试策略：单测/集成/e2e 的取舍（先小后大）
- 最小用例集：happy path + 关键错误场景（2-5 条）
- 验收 checklist：可执行步骤

## HTTP API 集成测试（推荐最小集：supertest 风格）

适用：Node.js 后端（Express/Fastify/Nest 等）

最小用例集建议（至少覆盖）：
- `/health` 返回 200（并包含版本/时间戳等可选字段）
- CRUD happy path（create/list/get/update/delete）
- 错误场景（至少 2 条）：
  - 400：输入校验失败（缺字段/类型不对）
  - 404：资源不存在

一致性要求：
- 错误返回结构统一（例如 `{ error: { code, message, details? } }`）
- 每个用例写清 Setup/Steps/Expected

落盘建议：
- 项目内测试文件（例如 `backend/test/*.spec.ts`）
- 并把“验收 checklist”摘要写入 `projects/<slug>/HANDOFF.md`

## 用例模板

```text
Case: <name>
- Setup:
- Steps:
- Expected:
- Notes:
```

## 参考（只读武器库）

- `references/lobehub/.agents/skills/testing/SKILL.md`
- `skills/agency-dev-team/souls/qa.md`
- `skills/agency-dev-team/souls/testing-api-tester.md`
