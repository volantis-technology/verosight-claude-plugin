---
description: Get trending posts and profiles from social media. Use when the user asks what's trending or popular.
allowed-tools: Bash(curl *)
---

# Trending Content

Get trending posts and profiles from the Verosight API.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/trending?days=7&limit=10" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `keyword` — optional, filter by topic
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "trending on tiktok" → platform=tiktok
- "trending this month" → days=30
- "trending about AI on twitter" → keyword=AI, platform=x

## Output Format

**Top Posts:** platform, author, content snippet, engagement, date.
**Top Profiles:** name, platform, total engagement, post count.

Show credits used (5 per call).
