手动接入：

在配置前，请确保清除以下 Anthropic 相关的环境变量，以免影响 MiniMax API 的正常使用：
- ANTHROPIC_AUTH_TOKEN
- ANTHROPIC_BASE_URL

注意：环境变量 `ANTHROPIC_AUTH_TOKEN` 和 `ANTHROPIC_BASE_URL` 优先级高于配置文件


MacOS & Linux 为 `~/.claude/settings.json`
Windows 为`用户目录/.claude/settings.json`
`MINIMAX_API_KEY` 需替换为您的 MiniMax API Key

```json
{
	"env": {
		"ANTHROPIC_BASE_URL": "https://api.minimaxi.com/anthropic",
		"ANTHROPIC_AUTH_TOKEN": "MINIMAX_API_KEY",
		"API_TIMEOUT_MS": "3000000",
		"CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": 1,
		"ANTHROPIC_MODEL": "MiniMax-M2.7",
		"ANTHROPIC_SMALL_FAST_MODEL": "MiniMax-M2.7",
		"ANTHROPIC_DEFAULT_SONNET_MODEL": "MiniMax-M2.7",
		"ANTHROPIC_DEFAULT_OPUS_MODEL": "MiniMax-M2.7",
		"ANTHROPIC_DEFAULT_HAIKU_MODEL": "MiniMax-M2.7"
	}
}
```

编辑或新增 `.claude.json` 文件
MacOS & Linux 为 `~/.claude.json`
Windows 为`用户目录/.claude.json`

```json
{
	"hasCompletedOnboarding": true
}
```














