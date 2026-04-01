# api_test_minset.md — HTTP API 最小测试集（集成测试/验收）

> 用途：为任何 REST API 提供最小可行的自动化/手工验收用例集。

## 前置

- Base URL：
- 认证方式（若有）：
- 测试数据清理策略：

## 1) Health

- Case: GET /health
  - Expected: 200
  - Body: 包含 `status`（可选：`version`、`uptime`）

## 2) CRUD Happy Path（以 <resource> 为例）

- Case: Create
  - POST /<resource>
  - Expected: 201 + 返回 id

- Case: List
  - GET /<resource>
  - Expected: 200 + 数组（或分页结构）

- Case: Get by id
  - GET /<resource>/:id
  - Expected: 200 + 对象

- Case: Update
  - PATCH/PUT /<resource>/:id
  - Expected: 200 + 更新后对象

- Case: Delete
  - DELETE /<resource>/:id
  - Expected: 204（或 200）

## 3) Error Contract（至少两条）

- Case: 400 validation
  - 缺少必填字段/类型错误
  - Expected: 400 + 统一错误结构（建议 `{ error: { code, message, details? } }`）

- Case: 404 not found
  - 使用不存在 id
  - Expected: 404 + 统一错误结构

## 4) 回归点（可选但推荐）

- 幂等性/重复提交
- 分页/排序/过滤
- 并发更新冲突（若存在）

## 5) 备注

- 自动化实现建议：Node 项目可采用 supertest 风格（对 server 直接发请求）
