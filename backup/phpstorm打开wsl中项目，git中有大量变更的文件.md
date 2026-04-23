## CRLF/LF
File → Settings → Editor → Code Style → Line separator  ：  Unix and macOS (\n) 
File Encodings  → Default line separator  ： LF

配置 Git 忽略行尾转换，在 WSL 终端里执行

    # 关闭自动转换行尾
    git config --global core.autocrlf false

    # 强制使用 LF
    git config --global core.eol lf

    # 忽略文件权限变化（第二个常见原因）
    git config --global core.filemode false

    # 强制重置工作区状态
    git checkout .    // git restore . 

## PhpStorm 用了 Windows 的 Git
File → Settings → Version Control → Git  ：`\\wsl.localhost\Ubuntu\user\bin\git`