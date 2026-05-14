---
description: Track follower and following growth over time for a profile. Use when the user asks about account growth.
allowed-tools: Bash(curl *)
---

# Growth Tracking

Track follower/following growth over time for a specific profile.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/growth?platform=PLATFORM&profile_name=NAME&days=30" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `platform` — required: x, instagram, tiktok, etc.
- `profile_name` — required: the profile to track
- `days` — period 1-90 (default 30)

Parse the user's request:
- "growth of @KompasTV on twitter" → platform=x, profile_name=KompasTV
- "instagram follower growth for nike last 3 months" → platform=instagram, profile_name=nike, days=90
- "how fast is CNN growing on tiktok" → platform=tiktok, profile_name=CNN

## Output Format

Timeline table (date, followers, following, change). Summarize total growth, average daily growth, notable spikes.

Show credits used (3 per call).
