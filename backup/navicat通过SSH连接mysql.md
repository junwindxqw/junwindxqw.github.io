>ssh的作用：无密登录服务器。
>ssh密钥相关文档：https://help.aliyun.com/zh/yunxiao/user-guide/configure-ssh-key

1. 本地生成 ssh 密钥对。
```
ssh-keygen -t ed25519 -C "<注释内容>"
```
2. 将公钥放入到服务器的这个文件中：~/.ssh/authorized_keys 
3. 使用私钥登录。

<img width="572" height="320" alt="Image" src="https://github.com/user-attachments/assets/f39fdd17-eeaa-4a6f-bca3-b1b40ee28b8d" />

<img width="642" height="380" alt="Image" src="https://github.com/user-attachments/assets/20b539f0-d50f-4541-901b-cbb407a78ed3" />