---
name: setup
description: Set up Verosight API access. Run this first to configure your API key.
user-invocable: true
allowed-tools: Bash, Read, Write
---

# Verosight Setup

Help the user set up Verosight API access. Follow these steps:

## Step 1: Check for existing API key

Check if the environment variable `VEROSIGHT_API_KEY` is set:
```bash
echo ${VEROSIGHT_API_KEY:+"Key is set: ${VEROSIGHT_API_KEY:0:12}..."}
echo ${VEROSIGHT_API_KEY:-"No key set"}
```

## Step 2: If no key, guide the user

Tell the user:
1. Sign up at https://verosight.com/register (free, 1,000 credits included)
2. Go to https://verosight.com/dashboard/keys and create an API key
3. Set the key: `export VEROSIGHT_API_KEY=vlt_live_YOUR_KEY`

Or add it permanently to their shell profile:
```bash
echo 'export VEROSIGHT_API_KEY=vlt_live_YOUR_KEY' >> ~/.zshrc
```

## Step 3: Verify the key works

```bash
curl -s https://api.verosight.com/v1/account/balance -H "X-API-Key: $VEROSIGHT_API_KEY"
```

Show the user their credit balance and tier.

## Step 4: Suggest MCP setup (optional)

For the best experience, suggest setting up the MCP server so all Verosight tools are available automatically:

**Remote SSE (recommended for Cursor/Windsurf):**
Add to `.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "verosight": {
      "url": "https://api.verosight.com/v1/mcp/sse",
      "headers": {
        "X-API-Key": "vlt_live_YOUR_KEY"
      }
    }
  }
}
```

**Local binary (for Claude Desktop):**
```bash
curl -fsSL https://verosight.com/download/mcp/install.sh | sh
```
