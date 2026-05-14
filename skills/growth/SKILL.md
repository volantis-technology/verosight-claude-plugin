---
name: growth
description: Track follower and following growth over time for a profile. Usage - /verosight:growth <platform> <profile> [days]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Growth Tracking

Track follower/following growth over time for a specific profile.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Parse the platform and profile name from the user's request.
3. Call the growth endpoint.
4. Present growth data as a timeline.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/growth?platform=PLATFORM&profile_name=NAME&days=30" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
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

Show a timeline:

| Date | Followers | Following | Change |
|------|-----------|-----------|--------|
| ... | ... | ... | +/- |

Summarize: total growth, average daily growth, any notable spikes or drops.

Show credits used (3 per call).
