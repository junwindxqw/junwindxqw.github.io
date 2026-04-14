> 声明 : 仅作学习测试用，请支持正版软件。

管理员身份打开 PowerShell（或 Windows 终端）
```
irm https://get.activated.win | iex
``` 
输入 1 → HWID 激活（数字许可证方式，永久激活 Windows）。
输入 2 → Office 激活


纯 CMD 的 KMS 激活：
```
slmgr /ipk W269N-WFGWX-YVC9B-4J6C9-T83GX
slmgr /skms kms.0t.net.cn
slmgr /ato
```
激活成功后，每 180 天可重新运行 slmgr /ato 续期