# Verosight Plugin Marketplace

Social media intelligence for Claude Code. Search posts, analyze sentiment, track trends, find experts, get AI recommendations, and compare profiles across X, Instagram, TikTok, Facebook, LinkedIn, YouTube, and news portals.

## Install

**Add the marketplace:**
```bash
claude plugin marketplace add volantis-technology/verosight-claude-plugin
```

**Install the plugin:**
```bash
claude plugin install verosight@verosight-marketplace
```

Or from within Claude Code:
```
/plugin marketplace add volantis-technology/verosight-claude-plugin
/plugin install verosight@verosight-marketplace
```

When you enable the plugin, you'll be prompted for your API key. Get one free at [verosight.com/register](https://verosight.com/register) (1,000 free credits).

## Skills

| Skill | Description | Credits |
|-------|-------------|---------|
| `/verosight:setup` | Verify API access | free |
| `/verosight:search <query>` | Search posts across platforms | 2 |
| `/verosight:trending [platform]` | Get trending content | 5 |
| `/verosight:sentiment <topic>` | Analyze public sentiment | 5 |
| `/verosight:sentiment-trend [keyword]` | Daily sentiment trend over time | 3 |
| `/verosight:topics [platform]` | Discover trending topic clusters | 5 |
| `/verosight:hashtags [keyword]` | Trending hashtags by engagement | 3 |
| `/verosight:mentions [keyword]` | Most-mentioned profiles | 3 |
| `/verosight:best-time [platform]` | Best posting times for engagement | 3 |
| `/verosight:engagement [platform]` | Rank profiles by engagement | 5 |
| `/verosight:growth <platform> <profile>` | Track follower growth | 3 |
| `/verosight:experts <query>` | Find topic experts by authority | 5 |
| `/verosight:profile <platform> <name>` | Get profile details and stats | 5 |
| `/verosight:compare <p1> vs <p2>` | Compare profile engagement | 5 |
| `/verosight:recommendations <category>` | AI recommendations from social buzz | 15 |
| `/verosight:chat <question>` | Ask AI any social media question | 20 |
| `/verosight:balance` | Check credit balance | free |

## Examples

```
/verosight:search posts about AI from last week
/verosight:trending on tiktok
/verosight:sentiment iran conflict
/verosight:sentiment-trend electric vehicles
/verosight:topics tech on twitter this month
/verosight:hashtags fashion on instagram
/verosight:mentions politics on x
/verosight:best-time when to post about technology on x
/verosight:engagement top profiles on tiktok
/verosight:growth x KompasTV
/verosight:experts AI on twitter
/verosight:profile x KompasTV
/verosight:compare KompasTV vs Metro_TV on twitter
/verosight:recommendations products trending in tech
/verosight:chat what's the public sentiment about electric vehicles this week?
/verosight:balance
```

## Semantic Keyword Filtering

Several analytics skills support **keyword-based semantic search** — add a topic and the API uses AI embeddings to find relevant posts before aggregating:

- `/verosight:sentiment-trend politics` — daily sentiment trend filtered to politics
- `/verosight:best-time technology on x` — best posting times for tech content
- `/verosight:hashtags AI` — hashtags most associated with AI conversations
- `/verosight:mentions crypto` — who gets mentioned most in crypto discussions

## Recommendation Categories

`products`, `movies`, `books`, `software`, `games`, `travel`, `skills`, `content`, `marketing`, `problems`

## Alternative: MCP Server

For a richer experience with all 19 tools available automatically, set up the MCP server:

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
- [Release Notes](https://verosight.com/release-notes)
