# AGENTS.md

本文件面向维护本 bucket 的 AI agent，记录通用规范与流程约束。

## 目录规范引用

- CI / workflow 约束：见 `.github/AGENTS.md`
- 文档维护约束：见 `doc/AGENTS.md`
- 各软件的特殊情况记录：`doc/bucket/<软件名>.md`

## 软件修改前置检查

修改某个软件的 manifest 之前，必须先查找 `doc/bucket/<manifest名>.md`
是否存在对应约束文档；存在则严格遵循其中的特殊写法要求。

## Manifest 变更规则

- 新增/更新软件时，hash 必须取自 release 资产的实际 SHA256
- checkver 统一用 GitHub API + jsonpath 取 `tag_name`，正则提取版本号
- manifest 与其对应的 `doc/bucket/` 文档、LOG.md 条目必须在同一个 commit 中提交
- 不在 AGENTS.md 与 README.md 中记录任何本机特定信息（绝对路径等），保证仓库可迁移

## 提交信息规范（精简版 Conventional Commits）

格式：`类型: 主题描述`（冒号后有空格，主题结尾不加句号）

| 类型 | 用途 |
|---|---|
| feat | 新增软件或新能力 |
| fix | 修复问题 |
| docs | 仅文档变更 |
| ci | workflow / 测试脚本变更 |
| chore | 杂项 |

改动逻辑复杂时，正文补充"为什么改"，不做钩子强制校验。

## 变更发布流程

1. 按上述规则完成本地修改与 commit
2. `git push` 到 origin master
3. 通过 GitHub API 轮询本次 run 至 completed，
   要求 conclusion 为 success 且 annotations 为空
4. 失败则修复后从第 2 步重走
5. 成功后在本地 scoop 的 bucket 副本目录执行 `git pull` 完成同步
