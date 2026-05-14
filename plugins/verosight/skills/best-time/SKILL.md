---
description: Find the best times to post for maximum engagement with optional topic filtering via semantic search. Use when the user asks when to post.
allowed-tools: Bash(curl *)
---

# Best Posting Time

Find the best times to post for maximum engagement. Supports keyword filtering for topic-specific optimal posting times.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/best-time?platform=x&days=30" \
  -H "X-API-Key: ${user_config.api_key}"
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

## Output Format

Heatmap or table by day of week and hour. Highlight top 3 optimal time slots with a recommendation.

Show credits used (3 per call).
