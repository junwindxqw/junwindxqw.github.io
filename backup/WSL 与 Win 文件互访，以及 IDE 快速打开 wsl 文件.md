> win 的磁盘挂载在 wsl 的 /mnt 下

## WSL → Windows
- 访问文件：`/mnt/c/`  ` /mnt/d/`
- 打开当前目录：`explorer.exe .`


## Windows → WSL
- 访问路径：`\\wsl.localhost`   `\\wsl$`

## wsl 中快捷使用 vscode 打开
```sh
code .    # 如果打不开，可以参考下面的phpstorm配置别名
code docker-compose.yml
```
或者直接在文件资源管理器中先打开wsl目录，然后右键菜单中选择vscode打开。

## wsl 中快捷使用 phpstorm 打开
```sh
phpstorm64.exe .     # 如果不能打开，我们在wsl中添加一个命令

# 配置别名
echo 'alias phpstorm="/mnt/d/mysoft/PhpStorm\ 2025.3.3/bin/phpstorm64.exe"' >> ~/.bashrc
source ~/.bashrc

phpstorm .
```






