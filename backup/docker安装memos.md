## 一键搞定版
```sh
 docker run -d \        后台运行 
  --name memos \      容器的名称
  --restart unless-stopped \      开机 / 崩溃自动重启
  -p 5230:5230 \       主机5230端口 ：映射到容器中5230端口
  -v ~/.memos/:/var/opt/memos \         数据持久化 主机~/.memos目录 ： 映射到容器/var/opt/memos
  neosmemo/memos:stable         镜像名称
```

## Docker Compose 版
```sh
# 创建目录
mkdir -p ~/docker/memos && cd ~/docker/memos

# 新建 docker-compose.yml
vim docker-compose.yml
```

docker-compose.yml 文件中的内容：
```yaml 
version: "3.8"  # 新版本这个字段已废弃，可以不加了

services:
  memos:    # memos服务
    image: neosmemo/memos:stable  # 镜像
    container_name: memos  # 容器名称
    restart: unless-stopped    # 挂掉了自动重启
    ports:    # 端口映射
      - "5230:5230"    # 本机端口：容器端口
    volumes:   # 数据卷
      - ./data:/var/opt/memos   # 数据持久化到当前目录 ./data       本机目录：容器目录
    environment:    # 环境变量
      - TZ=Asia/Shanghai   # 时区
```

```
# 后台启动（首次自动拉镜像）
docker compose up -d

# 查看运行状态
docker compose ps

# 查看日志（排错）
docker compose logs -f
```

## 访问
本地：http://localhost:5230
服务器：http://服务器IP:5230

首次访问会要求创建管理员账号（第一个用户就是管理员）


## docker compose 常用管理命令
```bash
# 停止
docker compose stop

# 启动
docker compose start

# 重启
docker compose restart

# 停止并删除容器（数据卷 ./data 不会删）
docker compose down

# 更新镜像（重新拉最新 stable）
docker compose pull && docker compose up -d
```


## 数据备份与迁移
- 数据全部在：./data（或你挂载的本地目录）
- 备份：直接打包 ./data 文件夹
- 迁移：把 ./data 复制到新服务器，用同样 docker-compose.yml 启动即可


## 常见问题
- 端口被占用：改端口：-p 5231:5230（宿主机端口改成 5231）
- 权限报错：给目录权限：chmod -R 755 ./data
- 国内拉镜像慢：可使用镜像：docker.xuanyuan.run/neosmemo/memos:stable

## 关于restart: unless-stopped配置项

<img width="549" height="459" alt="Image" src="https://github.com/user-attachments/assets/6f5b8944-3a0b-4d2b-b7aa-c79b4ba3ffa5" />

## docker compose up -d 和 docker compose start 区别？

docker compose start：只启动已存在的容器（不重建、不更新、不读新配置）

docker compose up -d：创建 / 重建 / 更新容器 + 启动（会读最新配置）

<img width="319" height="435" alt="Image" src="https://github.com/user-attachments/assets/a10b3dba-0c19-40fa-abb8-8a0e12dafaa2" />

<img width="444" height="556" alt="Image" src="https://github.com/user-attachments/assets/ac2bbc5c-430c-41fe-8feb-5a57b3cc03d7" />

日常重启（不改配置）docker compose restart

改了配置文件（比如端口、目录）docker compose up -d

更新 Memos 最新版    docker compose pull;    docker compose up -d

start = 只启动旧容器
up -d = 按最新配置重新创建并启动

注意：
docker compose up -d 不会自动下载新版镜像！
它只会用【本地已经有的镜像】来启动容器。


docker compose up -d  做的事情：
- 看你的 docker-compose.yml
- 用本地已有的镜像 启动 / 重建容器
- 它不会去 Docker 仓库检查有没有新版！它不会自动下载新版镜像！

docker compose pull 做什么？
专门去 Docker 仓库下载最新版镜像到本地。

所以更新镜像，需要：
```
docker compose pull      # 下载最新镜像到本地
docker compose up -d     # 用新镜像重建容器     docker compose pull && docker compose up -d
```

## docker compose up -d，docker compose start 是怎么知道处理的是哪个 docker-compose.yml 文件的？

它们默认只找【当前目录】下的 docker-compose.yml 文件。

没找到 → 直接报错：no configuration file provided

```bash
# 指定路径/文件
docker compose -f /path/to/docker-compose.yml up -d
```

以后你装很多服务（比如 Nextcloud、Bitwarden），每个都放单独文件夹：
```bash
cd ~/docker/memos && docker compose up -d → 管 Memos
cd ~/docker/nextcloud && docker compose up -d → 管 Nextcloud
```
