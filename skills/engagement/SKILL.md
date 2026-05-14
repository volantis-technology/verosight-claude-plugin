---
name: engagement
description: Rank profiles by engagement metrics. Usage - /verosight:engagement [platform] [days]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Engagement Ranking

Rank profiles by engagement using the Verosight API.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the engagement-ranking endpoint with filters.
3. Present a ranked list of profiles by engagement.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/engagement-ranking?days=7&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, filter by topic (e.g. "fashion", "politics")
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "top engagement on instagram" → platform=instagram
- "most engaging profiles about sports" → keyword=sports
- "engagement ranking this month" → days=30

## Output Format

For each profile:
- Rank
- Profile name and platform
- Total engagement (likes + comments + shares)
- Post count
- Average engagement per post

Show credits used (5 per call).
