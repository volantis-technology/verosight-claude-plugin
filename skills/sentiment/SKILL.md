---
name: sentiment
description: Analyze sentiment for a topic across social media. Usage - /verosight:sentiment <topic>
user-invocable: true
allowed-tools: Bash(curl *)
---

# Sentiment Analysis

Analyze public sentiment for a topic using the Verosight API.

User's query: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the sentiment endpoint with the user's topic.
3. Present a clear breakdown with percentages.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/sentiment?query=TOPIC&days=7" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `query` — required, the search term
- `days` — period 1-90 (default 7)
- `platform` — filter by platform
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "sentiment on iran" → query=iran
- "how do people feel about AI on twitter" → query=AI, platform=x
- "sentiment about elections last month" → query=elections, days=30

## Output Format

Show:
- Total posts analyzed
- Positive: count (percentage%)
- Negative: count (percentage%)
- Neutral: count (percentage%)
- A brief summary interpreting the results
- 1-2 sample positive posts (if available)
- 1-2 sample negative posts (if available)

Show credits used from meta.
