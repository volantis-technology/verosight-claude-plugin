---
name: best-time
description: Find the best times to post for maximum engagement, with optional topic filtering. Usage - /verosight:best-time [platform] [profile] [keyword]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Best Posting Time

Find the best times to post for maximum engagement using the Verosight API. Supports keyword filtering to analyze topic-specific optimal posting times.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the best-time endpoint.
3. Present a heatmap-style breakdown of best posting days and hours.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/best-time?platform=x&days=30" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `platform` — filter: x, instagram, tiktok, etc.
- `profile_name` — analyze a specific profile's posting pattern
- `keyword` — optional, analyze topic-specific posting times via semantic search
- `days` — period 1-90 (default 30)

Parse the user's request:
- "best time to post on twitter" → platform=x
- "when should I post about politics on X" → platform=x, keyword=politics
- "best posting time for @KompasTV" → platform=x, profile_name=KompasTV
- "kapan waktu terbaik posting tentang teknologi" → keyword=teknologi

## Output Format

Show a heatmap or table by day of week and hour:

| Day | Best Hours | Avg Engagement |
|-----|-----------|----------------|
| Monday | 9am, 7pm | ... |
| Tuesday | ... | ... |
| ... | ... | ... |

Highlight the top 3 optimal time slots and provide a recommendation.

Show credits used (3 per call).
