---
description: Discover trending topics and clusters from social media conversations. Use when the user asks what people are talking about.
allowed-tools: Bash(curl *)
---

# Trending Topics

Discover trending topics from social media using the Verosight API.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/topics?days=7&limit=10" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `keyword` — optional, filter posts by topic before clustering
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "topics on tiktok" → platform=tiktok
- "what are people talking about this month" → days=30
- "tech topics on twitter" → keyword=technology, platform=x

## Output Format

For each topic: label/keywords, post count, representative terms, sentiment breakdown if available.

Show credits used (5 per call).
