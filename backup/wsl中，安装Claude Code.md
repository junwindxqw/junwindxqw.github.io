```
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl git build-essential

curl -fsSL https://claude.ai/install.sh | bash    // 安装位置：~/.local/bin/claude

claude --version
```

<img width="721" height="375" alt="Image" src="https://github.com/user-attachments/assets/fdb424db-5116-4cc7-8a96-e02597b902a5" />


若提示 claude: command not found，执行：

```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

<img width="426" height="557" alt="Image" src="https://github.com/user-attachments/assets/78afe793-9032-42d0-832d-4c364dd89690" />
