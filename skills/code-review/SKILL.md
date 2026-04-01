# code-review

代码评审技能：把“看一眼”变成可验收的检查清单。

## 适用场景

- 任何 PR/大改动合入前
- 重要 bugfix、发布前回归
- 新模块/新依赖引入

## 输入

- 变更目标（为什么改）
- diff/patch 或涉及的文件列表
- 运行方式（本地启动/测试命令）

## 输出（必须包含）

1) TL;DR（是否建议合并：Yes/No/Block）
2) 风险分级：P0（阻塞）/P1（高）/P2（中）/P3（低）
3) 问题清单：按“正确性/安全/性能/可维护性/可测试性/可观测性/兼容性”分类
4) 建议修复：给出具体改法（能写 patch 就写 patch）
5) 验证步骤：如何确认修复有效

## 检查清单（最小可用）

### Correctness
- [ ] 需求覆盖了吗？边界/空值/异常路径处理了吗？
- [ ] 错误处理一致（错误码/消息结构/返回值）

### Security
- [ ] 输入校验/注入风险（SQL/NoSQL/命令注入）
- [ ] 敏感信息是否进入日志/前端
- [ ] 鉴权/权限检查是否绕过

### Performance
- [ ] N+1 / 多余请求 / 无缓存热点
- [ ] 大对象/大列表是否分页/限流

### Maintainability
- [ ] 命名、目录结构、重复代码
- [ ] 配置是否集中（env/example）

### Testability
- [ ] 至少有“怎么验证”的说明
- [ ] 关键逻辑是否有单测/集成测（可逐步补）

### Observability
- [ ] 关键路径日志、错误栈、request id

## 参考（只读武器库）

- `references/lobehub/.agents/skills/code-review/SKILL.md`
- `references/everything-claude-code/agents/code-reviewer.md`
