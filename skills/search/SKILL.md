---
name: search
description: Search social media posts across X, Instagram, TikTok, Facebook, LinkedIn, YouTube, and news portals. Usage - /verosight:search <query>
user-invocable: true
allowed-tools: Bash(curl *)
---

# Search Posts

Search for social media posts using the Verosight API.

The user's query is: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable for authentication.
2. Call the Verosight API to search posts matching the user's query.
3. Present results in a clean, readable format.

## API Call

```bash
curl -s "https://api.verosight.com/v1/posts?keyword=$QUERY&limit=10" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters you can use based on the user's request:**
- `keyword` — search term in post content
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `profile_name` — filter by author
- `date_from` / `date_to` — YYYY-MM-DD
- `min_likes` — minimum like count
- `sort` — posted_at, like_count, comment_count
- `order` — desc (default), asc
- `limit` — 1-100 (default 20)

Parse the user's natural language request to determine which parameters to use. For example:
- "posts about AI from last week" → keyword=AI, date_from=7 days ago
- "trending instagram posts about fashion" → keyword=fashion, platform=instagram, sort=like_count
- "what did @KompasTV post today" → profile_name=KompasTV, date_from=today

## Output Format

For each post, show:
- Platform and author
- Content (truncated to ~200 chars)
- Engagement: likes, comments, shares
- Posted date
- URL if available

Also show total results found and credits used from the meta.
