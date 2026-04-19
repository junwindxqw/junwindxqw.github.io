## 安装
```
sudo apt update
sudo apt install nginx -y
nginx -v    # 查看是否已安装
sudo systemctl status nginx   # 查看是否在运行
```
浏览器访问：http://localhost/
<img width="542" height="192" alt="Image" src="https://github.com/user-attachments/assets/bc4581f2-7f66-46f4-bf28-708cf47258cb" />

## 常用管理命令
```
# 启动 Nginx
sudo systemctl start nginx

# 停止 Nginx
sudo systemctl stop nginx

# 重启 Nginx（修改配置后必用）
sudo systemctl restart nginx

# 重新加载配置（不中断服务，推荐）
sudo systemctl reload nginx

# 设置开机自启
sudo systemctl enable nginx

# 取消开机自启
sudo systemctl disable nginx
```

## Nginx 核心文件路径
- 主配置文件：/etc/nginx/nginx.conf
    - 网站配置目录：/etc/nginx/sites-available/
    - 启用的网站配置：/etc/nginx/sites-enabled/
    - 默认网页根目录：/var/www/html/
- 日志目录：
     - 访问日志：/var/log/nginx/access.log
    - 错误日志：/var/log/nginx/error.log







