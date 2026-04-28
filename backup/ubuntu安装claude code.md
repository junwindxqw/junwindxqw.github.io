
    sudo apt update && sudo apt upgrade -y
    
    sudo apt install -y curl git build-essential
    
    curl -fsSL https://claude.ai/install.sh | bash    // 安装位置：~/.local/bin/claude
    
    claude --version

    若提示 claude: command not found，执行：

    echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc