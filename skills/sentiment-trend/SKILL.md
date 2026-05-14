---
name: sentiment-trend
description: Track daily sentiment trends over time, with optional keyword filtering via semantic search. Usage - /verosight:sentiment-trend [keyword] [platform]
user-invocable: true
allowed-tools: Bash(curl *)
---

# Sentiment Trend

Track daily sentiment trends over time using the Verosight API. Supports keyword-based semantic search to filter by topic.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the sentiment-trend endpoint.
3. Present a day-by-day breakdown of positive/negative/neutral sentiment.

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/sentiment-trend?days=7" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, filter by topic using semantic search (e.g. "electric vehicles", "politik indonesia")

Parse the user's request:
- "sentiment trend about AI" → keyword=AI
- "how has sentiment on politics changed this month" → keyword=politics, days=30
- "daily sentiment on twitter last 2 weeks" → platform=x, days=14
- "sentiment trend on electric vehicles" → keyword=electric vehicles

## Output Format

Show a day-by-day table:

| Date | Positive | Negative | Neutral |
|------|----------|----------|---------|
| ... | count | count | count |

Summarize the overall trend (improving, declining, stable) and highlight any notable spikes.

Show credits used (3 per call).
