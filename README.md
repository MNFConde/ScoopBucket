# ScoopBucket

由 AI agent 管理的个人 [Scoop](https://scoop.sh) bucket 仓库。

本仓库不只收录终端软件，GUI 安装型软件同样收录。

## 软件列表

| 软件 | 类型 | 说明 |
|---|---|---|
| [skills-manager](https://github.com/xingkongliang/skills-manager) | CLI | Skills Manager 命令行版，管理 AI agent skills |
| skills-manager-gui | GUI | Skills Manager 图形界面版（Tauri NSIS 安装器） |

## 使用方式

```
scoop bucket add mybucket https://github.com/MNFConde/ScoopBucket
scoop install mybucket/skills-manager
```

## 维护说明

- 推送后 CI 自动验证 manifest 规范、checkver 与 hash
- 每天 UTC 16:00 由 Excavator 自动探测上游新版本并更新 manifest
- 各软件的特殊约束记录在 `doc/bucket/` 下，修改前请先查阅
