---
name: trending
description: Get trending posts and profiles from social media. Usage - /verosight:trending [platform] [days]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Trending Content

Get trending posts and profiles from the Verosight API.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the trending endpoint with appropriate filters.
3. Present top posts and top profiles separately.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/trending?days=7&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, filter by topic (e.g. "politics", "AI")
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "trending on tiktok" → platform=tiktok
- "trending this month" → days=30
- "top 5 trending" → limit=5
- "trending about AI on twitter" → keyword=AI, platform=x

## Output Format

**Top Posts:**
For each post: platform, author, content snippet, engagement total, posted date.

**Top Profiles:**
For each profile: name, platform, total engagement, post count.

Show credits used from meta.
