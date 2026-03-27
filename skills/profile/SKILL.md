---
name: profile
description: Get social media profile details and engagement stats. Usage - /verosight:profile <platform> <username>
user-invocable: true
allowed-tools: Bash(curl *)
---

# Profile Intelligence

Get detailed profile information and engagement statistics.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Parse the platform and username from the user's request.
3. Fetch both profile details and engagement stats.
4. If the profile is not found (202 response), inform the user a crawl was triggered.

## API Calls

**Profile details:**
```bash
curl -s "https://api.verosight.com/v1/profiles/PLATFORM/USERNAME" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Engagement stats:**
```bash
curl -s "https://api.verosight.com/v1/profiles/PLATFORM/USERNAME/stats?days=7" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Platforms:** x, instagram, tiktok, facebook, linkedin, youtube, news_portal

Parse the user's request:
- "profile of @KompasTV on twitter" → platform=x, name=KompasTV
- "kompas.tv news portal stats" → platform=news_portal, name=kompas.tv
- "instagram profile fashionista" → platform=instagram, name=fashionista

## Output Format

**Profile:**
- Name, display name, bio
- Followers, following, total posts
- Verified status
- Last crawled date

**Stats (7 days):**
- Post count
- Total likes, comments, shares
- Average engagement per post
- Top post (if available)
- Media type breakdown
