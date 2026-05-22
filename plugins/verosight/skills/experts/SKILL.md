---
description: Find topic experts and thought leaders by authority score. Use when the user asks who are the experts or key voices on a topic.
allowed-tools: Bash(curl *)
---

# Find Experts

Find topic experts and thought leaders using the Verosight API.

User's query: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/experts?query=TOPIC&days=7&limit=10" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `query` — required, the topic to find experts for
- `days` — period 1-90 (default 7)
- `limit` — max results (default 10)
- `platform` — filter: x, instagram, tiktok, etc.
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "experts on AI" → query=AI
- "who talks about crypto on twitter" → query=crypto, platform=x
- "top climate voices this month" → query=climate, days=30

## Output Format

For each expert: profile name, platform, authority score, post count, total engagement, sample content.

Show credits used (5 per call).
