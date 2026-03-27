---
name: compare
description: Compare engagement between social media profiles. Usage - /verosight:compare <profile1> vs <profile2>
user-invocable: true
allowed-tools: Bash(curl *)
---

# Compare Profiles

Compare engagement metrics between two or more social media profiles.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Parse profile names and platforms from the request.
3. Call the compare endpoint.
4. Present a side-by-side comparison table.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/compare?profiles=PLATFORM:NAME1,PLATFORM:NAME2&days=7" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `profiles` — comma-separated platform:username pairs (e.g. `x:KompasTV,x:Metro_TV`)
- `days` — period 1-90 (default 7)

Parse the user's request:
- "compare KompasTV and Metro_TV" → profiles=x:KompasTV,x:Metro_TV
- "compare @nike vs @adidas on instagram" → profiles=instagram:nike,instagram:adidas
- "KompasTV vs CNN Indonesia on twitter last month" → profiles=x:KompasTV,x:CNNIndonesia, days=30

## Output Format

Show a comparison table:

| Metric | Profile 1 | Profile 2 |
|--------|-----------|-----------|
| Posts | ... | ... |
| Total Likes | ... | ... |
| Total Comments | ... | ... |
| Total Shares | ... | ... |
| Avg Engagement/Post | ... | ... |

Add a brief analysis of who's performing better and why.
