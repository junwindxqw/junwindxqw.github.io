## 安装

    sudo apt update && sudo apt upgrade -y
    
    sudo apt install -y curl git build-essential
    
    curl -fsSL https://claude.ai/install.sh | bash    // 安装位置：~/.local/bin/claude
    
    claude --version


若提示 claude: command not found，执行：

    echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc

## 接入 minimax

    nano ~/.claude/settings.json
    {
      "env": {
        "ANTHROPIC_BASE_URL": "https://api.minimaxi.com/anthropic",
    	"ANTHROPIC_AUTH_TOKEN": "xxxxxxx",
    	"API_TIMEOUT_MS": "3000000",
    	"CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": 1,
    	"ANTHROPIC_MODEL": "MiniMax-M2.7",
    	"ANTHROPIC_SMALL_FAST_MODEL": "MiniMax-M2.7",
    	"ANTHROPIC_DEFAULT_SONNET_MODEL": "MiniMax-M2.7",
    	"ANTHROPIC_DEFAULT_OPUS_MODEL": "MiniMax-M2.7",
    	"ANTHROPIC_DEFAULT_HAIKU_MODEL": "MiniMax-M2.7"
      }
    }
    
    nano ~/.claude.json
    {
      "hasCompletedOnboarding": true
    }