```powershell
// 安装wsl
wsl --install  （自动开启功能 + 安装默认 Ubuntu）

// 列出可在线安装的 Linux 发行版
wsl --list --online    // 简写 wsl -l -o

// 安装某台 Linux（例：Ubuntu-24.04）
wsl --install -d Ubuntu-24.04

// 列出已安装的
wsl -l -v

// 启动某台 Linux（进入默认发行版）
wsl
// 启动指定 Linux
wsl -d Ubuntu-24.04

// 停止所有已运行的Linux
wsl --shutdown

// 停止某台运行的Linux
wsl --terminate Ubuntu-24.04   // 简写  wsl -t Ubuntu-24.04

// 备份某台 Linux（导出为 .tar 文件）
wsl --export Ubuntu-24.04 D:\backup\ubuntu2404.tar

// 卸载某台Linux发行版（卸载前先停止运行）
wsl --unregister Ubuntu-24.04

// 导入备份好的某台 Linux（恢复系统）
wsl --import 新名称 安装路径 备份文件.tar  // 示例： wsl --import Ubuntu24 D:\WSL\Ubuntu24 D:\backup\ubuntu2404.tar
```