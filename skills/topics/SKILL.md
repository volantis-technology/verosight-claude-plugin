---
name: topics
description: Discover trending topics and clusters from social media conversations. Usage - /verosight:topics [platform] [days]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Trending Topics

Discover trending topics from social media using the Verosight API.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the topics endpoint with appropriate filters.
3. Present topics with their post counts and representative keywords.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/topics?days=7&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `keyword` — optional, filter posts by topic before clustering (e.g. "politics", "technology")
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "topics on tiktok" → platform=tiktok
- "what are people talking about this month" → days=30
- "tech topics on twitter" → keyword=technology, platform=x

## Output Format

For each topic:
- Topic label/keywords
- Post count
- Top representative terms
- Sentiment breakdown if available

Show credits used (5 per call).
