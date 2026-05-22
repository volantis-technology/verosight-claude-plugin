---
description: Get posting and comment volume broken down by day and platform. Use when the user asks about activity levels, post volume, or how active a topic is.
allowed-tools: Bash(curl *)
---

# Volume Analytics

Get total posting and comment volume broken down by day and by platform.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/volume?days=7" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `platform` — filter: x, instagram, tiktok, facebook, linkedin, youtube, news_portal
- `keyword` — optional, filter volume for a specific topic
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "how many posts this week" -> days=7
- "volume about AI on twitter" -> keyword=AI, platform=x
- "posting activity last month" -> days=30

## Output Format

**By day:** date, post count, comment count.
**By platform:** platform name, post count, comment count.
Summarize total volume and notable spikes.

Show credits used (3 per call).
