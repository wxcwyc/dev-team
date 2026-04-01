# typescript

TypeScript 工程规范技能：把 TS 相关的设计/实现/改动统一到可维护的约定。

## 适用场景

- 新增 TS 模块/SDK
- 重构类型定义
- 引入第三方库需要补类型

## 输出（必须包含）

- 类型边界：输入/输出 DTO、对外暴露的类型
- 约束：strictness、any 使用边界
- 风险点：类型收窄不正确、运行时与类型不一致

## 最小检查点

- [ ] 公共 API 不泄漏内部类型实现细节
- [ ] 不用 `any` 逃避（必要时用 `unknown` + type guard）
- [ ] 运行时校验与 TS 类型保持一致（必要时引入 zod 等）

## 参考（只读武器库）

- `references/lobehub/.agents/skills/typescript/SKILL.md`
