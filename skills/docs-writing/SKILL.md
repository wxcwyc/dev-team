# docs-writing

技术文档写作技能：把“写点 README”变成可维护的交付物体系。

## 适用场景
- 新项目启动（README/运行方式/目录说明）
- 交付/上线（Handoff/Release notes）
- 支持/排障（Runbook/FAQ）

## 输出（必须包含）
1) 目标读者（用户/开发者/运维/测试）
2) 快速开始（5-10 分钟跑起来）
3) 配置说明（env、端口、依赖）
4) 验证方式（命令/检查点）
5) 已知限制与风险

## 推荐落盘位置
- 项目运行：项目根 `README.md`
- 排障：workspace `docs/TROUBLESHOOTING.md`
- 命令速查：workspace `docs/COMMANDS.md`
- 交接：`projects/<slug>/HANDOFF.md`

## 参考（武器库）
- `references/lobehub/docs/`
- `references/everything-claude-code/TROUBLESHOOTING.md`
