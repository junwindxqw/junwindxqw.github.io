## 尾符（CRLF/LF）不一致
File → Settings → Editor → Code Style → Line separator  ：  Unix and macOS (\n) 

File Encodings  -> Default line separator  ： LF

配置 Git 忽略行尾转换，在 WSL 终端里执行：
```bash
# 关闭自动转换行尾
git config --global core.autocrlf false
# 强制使用 LF
git config --global core.eol lf
# 忽略文件权限变化（第二个常见原因）
git config --global core.filemode false
# 强制重置工作区状态
git checkout .    // git restore . 
```

## PhpStorm 用了 Windows 的 Git，而不是 WSL 里的 Git

File → Settings → Version Control → Git  ： 

<img width="768" height="88" alt="Image" src="https://github.com/user-attachments/assets/323a8a17-2488-44ce-83c9-81e99be64914" />

## PhpStorm 缓存或索引异常

点击 File → Invalidate Caches...，勾选 Clear file system cache and local history，然后重启 PhpStorm。

刷新 Git 状态 ： 重启后，在 PhpStorm 底部的 Git 工具窗口，点击 Refresh 按钮，强制同步状态。










