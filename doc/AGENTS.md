# doc/AGENTS.md

本文件约束 `doc/` 目录下文档的维护规则。

## 命名与组织

- `doc/bucket/` 下以 manifest 名命名文档（如 `skills-manager-gui.md`），
  一个软件一份，记录该软件 manifest 的特殊写法约束

## 创建时机

新增或修改软件时，若存在常规 manifest 写法无法表达、且未来维护者
容易踩坑的约束（安装器参数、shim 冲突、特殊 URL 形式等），
必须建立对应文档。

## 同步要求

- manifest 与其对应的 `doc/bucket/` 文档必须在同一个 commit 中提交
- 文档内容保持精炼，只记录"为什么必须这样写"，不复述 manifest 本身
