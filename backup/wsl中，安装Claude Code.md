## 安装
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

## 常见的一些问题
<img width="426" height="557" alt="Image" src="https://github.com/user-attachments/assets/78afe793-9032-42d0-832d-4c364dd89690" />

## 接入 minimax
```sh
# 打开配置文件（不存在则自动创建）
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
```
关闭终端重新打开生效
