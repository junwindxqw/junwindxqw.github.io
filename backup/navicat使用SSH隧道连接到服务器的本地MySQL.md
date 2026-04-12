ssh的作用：无密登录服务器。
ssh密钥相关文档：https://help.aliyun.com/zh/yunxiao/user-guide/configure-ssh-key

1. 本地生成 ssh 密钥对。
```
ssh-keygen -t ed25519 -C "<注释内容>"    // 一路回车即可，密钥默认生成路径：/home/user/.ssh/id_ed25519，公钥与之对应为：/home/user/.ssh/id_ed25519.pub。
```
2. 将公钥放入到服务器的这个文件中：~/.ssh/authorized_keys ，一行放一个公钥。
3. 使用私钥登录。

<img width="572" height="320" alt="Image" src="https://github.com/user-attachments/assets/f39fdd17-eeaa-4a6f-bca3-b1b40ee28b8d" />

<img width="642" height="380" alt="Image" src="https://github.com/user-attachments/assets/20b539f0-d50f-4541-901b-cbb407a78ed3" />

踩坑：
权限问题：700 .ssh + 600 authorized_keys
authorized_keys文件不存在，手动创建。
```
mkdir -p ~/.ssh
vim ~/.ssh/authorized_keys

systemctl restart sshd
```