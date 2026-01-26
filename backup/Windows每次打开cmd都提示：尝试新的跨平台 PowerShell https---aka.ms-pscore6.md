phpstorm中每次打开terminal，都会有这个提示

<img width="567" height="109" alt="Image" src="https://github.com/user-attachments/assets/d8e0ba66-9cce-4eb5-8bab-36332c87ec5a" />

很烦这个提示，于是我搜了下这个是要做什么。

你现在用的 Windows PowerShell 是基于 .NET Framework 开发的，仅限 Windows 系统，且微软对它的更新仅以安全维护为主，不再添加新功能。

提示里的 PowerShell Core（现在统一叫 PowerShell 7+）是基于 .NET Core/.NET 6+ 开发的跨平台版本，支持 Windows、macOS、Linux 三大系统，并且会持续更新新特性（比如更好的 CLI 兼容性、更快的执行速度、更多内置命令）。

微软在 Windows PowerShell 的启动脚本里内置了这个提示，目的是引导用户迁移到功能更完善的跨平台版本，它不会影响你当前命令的执行，只是一个推荐性的提醒。

直接升级：
```
// 搜索PowerShell的最新版本
winget search --id Microsoft.PowerShell

// 安装
winget install --id Microsoft.PowerShell --source winget

// 安装预览版
winget install --id Microsoft.PowerShell.Preview --source winget

// 验证安装
pwsh -v
PowerShell 7.5.4
```

再次从phpstorm中打开，还是会有烦人的提示，我们此时需要切换终端。

<img width="803" height="344" alt="Image" src="https://github.com/user-attachments/assets/4bcb9fe5-5823-4bd6-aa9b-e5a976fd7b78" />

再次重新打开terminal，解决了

<img width="443" height="130" alt="Image" src="https://github.com/user-attachments/assets/5c501e7a-27d3-486e-bd53-5c96173cd8c6" />



