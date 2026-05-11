```
# 1. 执行官方安装脚本
irm https://claude.ai/install.ps1 | iex

# 2. 验证安装
claude --version
```

接入国模，主要修改两处配置
- 用户目录/.claude/settings.json
```
{
  "env": {
    "ANTHROPIC_BASE_URL": "BASE_URL",
    "ANTHROPIC_AUTH_TOKEN": "MIMO_API_KEY",
    "ANTHROPIC_MODEL": "mimo-v2.5-pro",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "mimo-v2.5-pro",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "mimo-v2.5-pro",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "mimo-v2.5-pro"
  }
}
```
- 用户目录/.claude.json
```
{
  "hasCompletedOnboarding": true
}
```
