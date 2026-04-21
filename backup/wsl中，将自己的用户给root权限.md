## 加入 sudo 用户组
sudo 组的所有成员都拥有完整的管理员权限

```
sudo usermod -aG sudo xqw   // 关闭当前 WSL 终端窗口，重新打开，使组权限生效

sudo whoami   验证权限
```

## 编辑 /etc/sudoers 文件

```
sudo visudo

root    ALL=(ALL:ALL) ALL
xqw     ALL=(ALL:ALL) ALL     // xqw     ALL=(ALL:ALL) NOPASSWD: ALL
```
若用 nano：按 Ctrl+O 保存 → Ctrl+X 退出