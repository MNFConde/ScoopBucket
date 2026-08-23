# LOG

## 日志维护规则

- 新记录一律插入所有日志的最上方（最新在前）
- 已提交的日志只能新增、不能修改，尤其禁止改动过往记录
- 尚未提交的当前条目可在同一条内直接订正
- 每条记录不超过 100 字

## 2026-08-23

- 建立 bucket：git init，注册本地 scoop，新增 skills-manager 与 skills-manager-gui 两个 manifest 并完成安装验证
- 修复 GUI 安装失败：此版 scoop 不自动运行 exe 安装器，manifest 显式声明 NSIS 静默参数 /S 与 /D=$dir
- GUI 主程序与 CLI shim 同名冲突，移除 GUI manifest 的 bin 字段仅保留 shortcuts
- 新增 CI 与 Excavator workflow（参考官方 Main），推送后自动校验 manifest，每日定时探测上游更新
- excavator cron 由每 4 小时改为每天 UTC 16:00（北京时间 0 点）
- 修复 CI 假绿：锁定 Pester 5.7.1 规避 Pester 6 空 TestCases 报错；test.ps1 退出码计入容器失败；checkout 升 v5
- 新增 README、AGENTS.md、doc/ 文档体系与 .github/AGENTS.md，固化 agent 规范与发布流程
