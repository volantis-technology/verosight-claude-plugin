---
description: Find the most-mentioned profiles in social media conversations with optional keyword filtering. Use when the user asks who is being talked about.
allowed-tools: Bash(curl *)
---

# Most-Mentioned Profiles

Find the most-mentioned profiles. Supports keyword-based semantic search to find mentions within a specific topic.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/mentions?days=7&limit=10" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `limit` — max results (default 20)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, find mentions in topic-relevant posts via semantic search
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "who gets mentioned most about politics" → keyword=politics
- "most mentioned accounts on twitter" → platform=x
- "mentions in tech conversations this month" → keyword=technology, days=30

## Output Format

For each profile: name, mention count, platform, context.

Show credits used (3 per call).
