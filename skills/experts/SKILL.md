---
name: experts
description: Find topic experts and thought leaders by authority score. Usage - /verosight:experts <query>
user-invocable: true
allowed-tools: Bash(curl *)
---

# Find Experts

Find topic experts and thought leaders using the Verosight API.

User's query: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the experts endpoint with the user's topic query.
3. Present experts ranked by authority score.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/experts?query=TOPIC&days=7&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `query` — required, the topic to find experts for
- `days` — period 1-90 (default 7)
- `limit` — max results (default 10)
- `platform` — filter: x, instagram, tiktok, etc.
- `exclude_profiles` — comma-separated profiles to exclude (e.g. news portals)
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "experts on AI" → query=AI
- "who talks about crypto on twitter" → query=crypto, platform=x
- "top climate voices this month" → query=climate, days=30

## Output Format

For each expert:
- Profile name and platform
- Authority score
- Post count on the topic
- Total engagement
- Sample content snippet

Show credits used (5 per call).
