```
PS C:\Users\xqw> wsl -l -v
  NAME              STATE           VERSION
* Ubuntu-24.04      Running         2       // docker client
  docker-desktop    Running         2      // dockerd server
```

Use the WSL 2 based engine 
- 让 Docker 运行在 WSL2 的虚拟机里，而不是 Windows 原生虚拟机。

*Add the .docker.internal names to the host’s /etc/hosts file 
- 让 Windows 宿主机能用 host.docker.internal 这种域名访问

Enable integration with my default WSL distro
- 启用了这个后，其它的wsl系统中，可直接使用docker命令