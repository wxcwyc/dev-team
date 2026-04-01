# api-contract

API 合同技能：先统一接口与数据结构，再并行前后端，减少返工。

## 适用场景
- 前后端并行开发
- 外部集成（第三方/SDK）
- 需要稳定错误码/分页/过滤约定

## 输出（必须包含）
- 资源模型：字段、必填、默认值、校验规则
- 路由表：method + path + request/response
- 错误约定：错误码/错误结构
- 示例：curl（至少 2-3 个关键接口）
- 版本策略（可选）：v1/v2 或兼容声明

## 推荐落盘
- `projects/<slug>/DECISIONS.md`：记录合同关键决策
- `docs/` 或项目 `docs/api.md`：完整合同文本

## 参考（武器库）
- `references/lobehub/docs/`（其文档组织方式）
