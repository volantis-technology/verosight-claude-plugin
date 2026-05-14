---
name: hashtags
description: Discover trending hashtags ranked by engagement, with optional keyword filtering. Usage - /verosight:hashtags [keyword] [platform]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Trending Hashtags

Discover trending hashtags ranked by engagement using the Verosight API. Supports keyword-based semantic search to find hashtags related to a specific topic.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the hashtags endpoint.
3. Present hashtags ranked by engagement.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/hashtags?days=7&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, find hashtags in topic-relevant posts via semantic search

Parse the user's request:
- "trending hashtags about fashion" → keyword=fashion
- "popular hashtags on tiktok" → platform=tiktok
- "hashtags related to AI this month" → keyword=AI, days=30

## Output Format

For each hashtag:
- Hashtag name
- Post count
- Total engagement
- Average engagement per post

Show credits used (3 per call).
