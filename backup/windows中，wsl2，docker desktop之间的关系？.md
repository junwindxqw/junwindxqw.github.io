<img width="944" height="284" alt="Image" src="https://github.com/user-attachments/assets/754fb54b-fa6e-4c95-8cc0-28d510f43676" />


Use the WSL 2 based engine ： 让 Docker 运行在 WSL2 的虚拟机里，而不是 Windows 原生虚拟机。

装的 Docker Desktop 其实是个 “外壳”
真正跑 Docker 服务（dockerd）、跑容器的环境
→ 是 WSL2 里的一个小型 Linux（也就是wsl -l -v看到的 docker-desktop， 这个虚拟机中安装了dockerd服务）

为什么要使用wsl2？
- WSL2 比旧版 Hyper-V 环境更快、兼容性更好
- 其它的wsl2都可以使用docker客户端服务， 自动请求到 docker-desktop 这台wsl 的 dockerd服务（不过需要开启一个配置，下面讲到）。

*Add the .docker.internal names to the host’s /etc/hosts file  ： 让 Windows 宿主机能用 host.docker.internal 这种域名访问 Docker 环境。

容器内部本来就能用 host.docker.internal
但这个配置是为了让 Windows 本身 也能解析这个域名
Docker 会自动往 Windows 的 hosts 文件写一行：192.168.65.2  host.docker.internal

为什么要勾？
你在 Windows 浏览器访问容器服务
比如：http://host.docker.internal:8080
你在 WSL2 访问 Windows 本地服务
否则你必须用 IP 而不能用名字


两个配置的关系总结
第一个：决定 Docker 是跑在 WSL2 里（你现在的情况）
第二个：决定 Windows 能不能用 host.docker.internal 访问 Docker 环境

<img width="888" height="327" alt="Image" src="https://github.com/user-attachments/assets/9e19027f-5fcd-4ef2-bfc4-b45874593958" />


Enable integration with my default WSL distro： 
- 它会自动把 Docker 服务（/var/run/docker.sock） 共享给你当前默认的那个 WSL 系统。
- 同时也会把 docker 客户端命令 安装到默认的 WSL 系统里。

Ubuntu-24.04 (下方的独立开关) 
对 非默认 的 WSL 系统起作用，当你电脑里装了不止一个 WSL 系统（比如 Ubuntu 22.04、Debian、Kali），你可以用这个开关，单独决定 哪个非默认系统 也能连上 Docker。