---
name: mentions
description: Find the most-mentioned profiles in social media conversations, with optional keyword filtering. Usage - /verosight:mentions [keyword] [platform]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Most-Mentioned Profiles

Find the most-mentioned profiles using the Verosight API. Supports keyword-based semantic search to find mentions within a specific topic.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the mentions endpoint.
3. Present profiles ranked by mention count.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/mentions?days=7&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, find mentions in topic-relevant posts via semantic search

Parse the user's request:
- "who gets mentioned most about politics" → keyword=politics
- "most mentioned accounts on twitter" → platform=x
- "mentions in tech conversations this month" → keyword=technology, days=30

## Output Format

For each profile:
- Profile name
- Mention count
- Platform
- Context (what they're being mentioned for, if discernible)

Show credits used (3 per call).
