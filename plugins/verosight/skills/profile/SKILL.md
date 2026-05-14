---
description: Get social media profile details and engagement stats. Use when the user asks about a specific account or profile.
allowed-tools: Bash(curl *)
---

# Profile Intelligence

Get detailed profile information and engagement statistics.

User's request: $ARGUMENTS

## API Calls

**Profile details:**
```bash
curl -s "https://api.verosight.com/v1/profiles/PLATFORM/USERNAME" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Engagement stats:**
```bash
curl -s "https://api.verosight.com/v1/profiles/PLATFORM/USERNAME/stats?days=7" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Platforms:** x, instagram, tiktok, facebook, linkedin, youtube, news_portal

Parse the user's request:
- "profile of @KompasTV on twitter" → platform=x, name=KompasTV
- "kompas.tv news portal stats" → platform=news_portal, name=kompas.tv
- "instagram profile fashionista" → platform=instagram, name=fashionista

If profile returns 202, a crawl was triggered — inform the user.

## Output Format

**Profile:** name, display name, bio, followers, following, total posts, verified status.
**Stats (7 days):** post count, likes/comments/shares, avg engagement per post, top post.
