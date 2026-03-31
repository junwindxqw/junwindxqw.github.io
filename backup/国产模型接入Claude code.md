安装cc，获取api key

在~/.claude.json 中，加入设置 "hasCompletedOnboarding": true，以跳过登录步骤。

~/.claude/settings.json
```
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.xiaomimimo.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "$MIMO_API_KEY",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "mimo-v2-pro",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "mimo-v2-pro",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "mimo-v2-pro"
  }
}
```
