---
description: Rank profiles by engagement metrics. Use when the user asks who has the most engagement or top performing accounts.
allowed-tools: Bash(curl *)
---

# Engagement Ranking

Rank profiles by engagement using the Verosight API.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/engagement-ranking?days=7&limit=10" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, filter by topic
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "top engagement on instagram" → platform=instagram
- "most engaging profiles about sports" → keyword=sports
- "engagement ranking this month" → days=30

## Output Format

For each profile: rank, name, platform, total engagement, post count, average engagement per post.

Show credits used (5 per call).
