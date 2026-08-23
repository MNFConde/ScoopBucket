# .github/AGENTS.md

本文件记录 CI / workflow 相关的约束，供 AI agent 维护时遵循。

## Pester 版本锁定

- `ci.yml` 中 psmodulecache 必须锁定 `Pester:5.7.1`
- 原因：Pester 6 将空 `-TestCases` 从静默跳过改为 discovery 抛错，
  而 scoop 核心的 `Import-Bucket-Tests.ps1` 在 commit 不含 JSON 变更时
  会传入空数组，导致 discovery 失败（上游 issue #6713 / #6693，均未修复）

## 假绿防护

- `bin/test.ps1` 的退出码为
  `FailedCount + FailedBlocksCount + FailedContainersCount`
- 容器级失败不计入 FailedCount，若回退为仅用 FailedCount 会重新引入假绿

## Excavator 定时任务

- cron 为 `0 16 * * *`（UTC 16:00，北京时间 0 点）
- 手动触发使用 workflow_dispatch；不监听 push 事件
