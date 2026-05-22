---
description: Search comments across all platforms. Use when the user wants to find comments about a topic, on a specific post, or from a specific author.
allowed-tools: Bash(curl *)
---

# Search Comments

Search comments across all social media platforms.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/comments?keyword=QUERY&limit=20" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `keyword` — search term in comment content
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `post_owner` — filter by original post author
- `date_from` / `date_to` — YYYY-MM-DD
- `limit` — 1-100 (default 20)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "comments about AI" -> keyword=AI
- "comments on KompasTV posts" -> post_owner=KompasTV
- "instagram comments about fashion" -> keyword=fashion, platform=instagram

## Output Format

For each comment: platform, author, content (~200 chars), like count, post author, date.

Show total results and credits used (2 per call).
