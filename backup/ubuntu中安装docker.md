1. 先检查systemd是否开启，/etc/wsl.conf 中 systemd=true 
```
wsl --terminate Ubuntu   终止
wsl -d Ubuntu   重启
ps -p 1 -o comm=      # 验证 systemd 是否生效，输出 systemd 即成功
```

2. 如果已经安装了docker，可以先卸载
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

3. 更新索引并安装依赖
```
sudo apt update && sudo apt upgrade -y
sudo apt-get install ca-certificates curl gnupg
```

4. 添加 Docker 官方 GPG 密钥（使用阿里云镜像）
```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://mirrors.aliyun.com/docker-ce/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

5. 添加 Docker 软件源
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://mirrors.aliyun.com/docker-ce/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

6. 安装 Docker
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

7. 配置 Docker 镜像加速器
建议配置多个备用地址或使用个人的阿里云加速器。
建议优先去 阿里云容器镜像服务 获取你的专属加速链接
```
sudo mkdir -p /etc/docker
sudo nano /etc/docker/daemon.json
{
  "registry-mirrors": [
    "https://mirror.baidubce.com",
    "https://docker.m.daocloud.io",
    "https://dockerproxy.com",
    "https://docker.nju.edu.cn"
  ]
}
```
提示：在 Nano 编辑器中，按 Ctrl + O 保存，Enter 确认，Ctrl + X 退出。
重启 Docker 服务
```
sudo systemctl daemon-reload
sudo systemctl restart docker
```

8. 管理权限与自启
免 sudo 运行：为了避免每次执行 docker 都要加 sudo，将当前用户加入 docker 组：
```
sudo usermod -aG docker $USER
```
注意： 执行完此命令后，需要关闭并重新打开 WSL 终端才能生效。

验证安装
```
docker pull hello-world
```

https://gemini.google.com/share/fb28076fe16b













