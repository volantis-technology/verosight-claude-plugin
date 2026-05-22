---
description: Analyze public sentiment for a topic across social media. Use when the user asks how people feel about something.
allowed-tools: Bash(curl *)
---

# Sentiment Analysis

Analyze public sentiment for a topic using the Verosight API.

User's query: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/sentiment?query=TOPIC&days=7" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `query` — required, the search term
- `days` — period 1-90 (default 7)
- `platform` — filter by platform
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "sentiment on iran" → query=iran
- "how do people feel about AI on twitter" → query=AI, platform=x
- "sentiment about elections last month" → query=elections, days=30

## Output Format

Show: total posts, positive/negative/neutral counts with percentages, brief summary, 1-2 sample posts per sentiment.

Show credits used (5 per call).
