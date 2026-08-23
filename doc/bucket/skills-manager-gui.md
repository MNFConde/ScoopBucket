# skills-manager-gui

GUI 版，Tauri NSIS 安装器（`_x64-setup.exe`），有两条硬性约束。

## 约束

- 必须显式声明安装参数：
  `"installer": {"args": ["/S", "/D=$dir"]}`
  原因：当前 scoop 版本对 exe 安装器既不解压也不自动运行，
  不写 installer 字段会导致安装后目录为空
- 禁止添加 `bin` 字段
  原因：GUI 主程序名为 `skills-manager.exe`，与 CLI 版的 shim 同名，
  添加会覆盖 CLI 命令；只保留 `shortcuts` 即可

## 已验证

- Tauri NSIS 静默安装 `/S` + `/D=` 兼容正常
- 安装目录内含 `skills-manager.exe`、`skills-manager-cli.exe`、
  `uninstall.exe`，shortcuts 指向主程序
