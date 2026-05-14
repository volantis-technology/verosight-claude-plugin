---
description: Search social media posts across X, Instagram, TikTok, Facebook, LinkedIn, YouTube, and news portals. Use when the user wants to find posts about a topic, person, or event.
allowed-tools: Bash(curl *)
---

# Search Posts

Search for social media posts using the Verosight API.

The user's query is: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/posts?keyword=$QUERY&limit=10" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `keyword` — search term in post content
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `profile_name` — filter by author
- `date_from` / `date_to` — YYYY-MM-DD
- `min_likes` — minimum like count
- `sort` — posted_at, like_count, comment_count
- `order` — desc (default), asc
- `limit` — 1-100 (default 20)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "posts about AI from last week" → keyword=AI, date_from=7 days ago
- "trending instagram posts about fashion" → keyword=fashion, platform=instagram, sort=like_count
- "what did @KompasTV post today" → profile_name=KompasTV, date_from=today

## Output Format

For each post: platform, author, content (~200 chars), engagement (likes/comments/shares), date, URL.

Show total results and credits used (2 per call).
