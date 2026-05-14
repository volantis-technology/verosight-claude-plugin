---
description: Verify Verosight API access and show account status. Run this to check your connection.
disable-model-invocation: true
allowed-tools: Bash(curl *)
---

# Verosight Setup

Verify the user's Verosight API connection.

## Verify the key works

```bash
curl -s https://api.verosight.com/v1/account/balance \
  -H "X-API-Key: ${user_config.api_key}"
```

Show the user their credit balance and tier.

If the key is not working, tell the user to:
1. Sign up at https://verosight.com/register (free, 1,000 credits included)
2. Go to https://verosight.com/dashboard/keys and create an API key
3. Re-enable the plugin with `/plugin` and enter the correct key

## Suggest MCP setup (optional)

For the best experience with all 19 tools available automatically, suggest setting up the MCP server:

**Remote SSE (recommended for Cursor/Windsurf):**
```json
{
  "mcpServers": {
    "verosight": {
      "url": "https://api.verosight.com/v1/mcp/sse",
      "headers": { "X-API-Key": "YOUR_KEY" }
    }
  }
}
```

**Local binary (for Claude Desktop):**
```bash
curl -fsSL https://verosight.com/download/mcp/install.sh | sh
```
