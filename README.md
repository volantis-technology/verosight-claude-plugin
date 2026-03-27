# Verosight Claude Code Plugin

Social media intelligence at your fingertips. Search posts, analyze sentiment, track trends, and compare profiles across X, Instagram, TikTok, Facebook, LinkedIn, YouTube, and news portals — all from Claude Code.

## Install

```bash
claude /plugin install https://github.com/volantis-technology/verosight-claude-plugin
```

## Setup

1. Get a free API key at [verosight.com/register](https://verosight.com/register) (1,000 free credits)
2. Set your key: `export VEROSIGHT_API_KEY=vlt_live_YOUR_KEY`
3. Run `/verosight:setup` to verify

## Skills

| Command | Description |
|---------|-------------|
| `/verosight:setup` | Configure API key and verify access |
| `/verosight:search <query>` | Search posts across platforms |
| `/verosight:trending [platform]` | Get trending content |
| `/verosight:sentiment <topic>` | Analyze public sentiment |
| `/verosight:profile <platform> <name>` | Get profile details and stats |
| `/verosight:compare <profile1> vs <profile2>` | Compare profile engagement |
| `/verosight:balance` | Check credit balance |

## Examples

```
/verosight:search posts about AI from last week
/verosight:trending on tiktok
/verosight:sentiment iran conflict
/verosight:profile x KompasTV
/verosight:compare KompasTV vs Metro_TV on twitter
/verosight:balance
```

## Credits

Each skill call costs API credits (same as direct API usage):
- Search, posts: 2 credits
- Trending, sentiment, topics: 5 credits
- Profile stats: 5 credits
- Compare: 5 credits
- Balance: free

Free accounts start with 1,000 credits. [Purchase more](https://verosight.com/dashboard/billing).

## Alternative: MCP Server

For a richer experience with all 13 tools available automatically, set up the MCP server:

**Remote SSE (Cursor/Windsurf):**
```json
{
  "mcpServers": {
    "verosight": {
      "url": "https://api.verosight.com/v1/mcp/sse",
      "headers": { "X-API-Key": "vlt_live_YOUR_KEY" }
    }
  }
}
```

**Local binary (Claude Desktop):**
```bash
curl -fsSL https://verosight.com/download/mcp/install.sh | sh
```

## Links

- [API Docs](https://verosight.com/docs)
- [Dashboard](https://verosight.com/dashboard)
- [MCP Setup Guide](https://verosight.com/docs#mcp)
