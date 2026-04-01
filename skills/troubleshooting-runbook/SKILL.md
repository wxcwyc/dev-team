# troubleshooting-runbook

排障/Runbook 技能：把问题处理变成可复现、可沉淀、可回归的手册化流程。

## 适用场景
- 启动失败/依赖服务异常
- 线上 5xx/超时
- 数据库连接/鉴权/配置错误

## 输出（必须包含）
- 症状（用户看到什么）
- 最短路径（3-5 步）
- 常见原因（按概率）
- 收集信息（命令/日志/环境）
- 修复与验证
- 回归点（避免复发）

## 强制落盘
- 必须更新 `docs/TROUBLESHOOTING.md`（新增章节或扩展已有）

## 模板
- 使用 `skills/agency-dev-team/templates/support_runbook.md`

## 参考（武器库）
- `references/lobehub/docs/`（大量 troubleshooting 写法）
- `references/everything-claude-code/TROUBLESHOOTING.md`
