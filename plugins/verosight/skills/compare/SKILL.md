---
description: Compare engagement between social media profiles. Use when the user wants to compare two or more accounts.
allowed-tools: Bash(curl *)
---

# Compare Profiles

Compare engagement metrics between two or more social media profiles.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/compare?profiles=PLATFORM:NAME1,PLATFORM:NAME2&days=7" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `profiles` — comma-separated platform:username pairs (e.g. `x:KompasTV,x:Metro_TV`)
- `days` — period 1-90 (default 7)

Parse the user's request:
- "compare KompasTV and Metro_TV" → profiles=x:KompasTV,x:Metro_TV
- "compare @nike vs @adidas on instagram" → profiles=instagram:nike,instagram:adidas
- "KompasTV vs CNN Indonesia last month" → profiles=x:KompasTV,x:CNNIndonesia, days=30

## Output Format

Side-by-side comparison table (posts, likes, comments, shares, avg engagement). Brief analysis of who's performing better.

Show credits used (5 per call).
