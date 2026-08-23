# skills-manager

CLI 版，单文件便携 exe，无特殊安装逻辑。

## 约束

- URL 使用 `#/skills-manager.exe` 将下载文件重命名，
  保证 shim 生成的命令名固定
- `bin` 用数组形式 `[["skills-manager.exe", "skills-manager"]]`
  注册命令别名
