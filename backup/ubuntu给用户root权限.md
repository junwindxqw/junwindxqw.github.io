```
sudo -i   // 切换到root用户

visudo -f /etc/sudoers.d/xqw
    xqw ALL=(ALL) NOPASSWD: ALL    // 填入

nano保存退出 ： ctrl + o  -> 回车 -> ctrl + x

chmod 440 /etc/sudoers.d/xqw
su - xqw
sudo whoami 
sudo apt update
```