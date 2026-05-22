---
description: Track daily sentiment trends over time with optional keyword filtering via semantic search. Use when the user asks how sentiment has changed over a period.
allowed-tools: Bash(curl *)
---

# Sentiment Trend

Track daily sentiment trends over time. Supports keyword-based semantic search to filter by topic.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/analytics/sentiment-trend?days=7" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Parameters:**
- `days` — period 1-90 (default 7)
- `platform` — filter: x, instagram, tiktok, etc.
- `keyword` — optional, filter by topic using semantic search (e.g. "electric vehicles", "politik indonesia")
- `media_type` — filter: image, video, text, article (photo is alias for image)
- `exclude_profiles` — comma-separated profiles to exclude
- `exclude_keywords` — comma-separated keywords to exclude

Parse the user's request:
- "sentiment trend about AI" → keyword=AI
- "how has sentiment on politics changed this month" → keyword=politics, days=30
- "daily sentiment on twitter last 2 weeks" → platform=x, days=14

## Output Format

Day-by-day table with positive/negative/neutral counts. Summarize the overall trend and notable spikes.

Show credits used (3 per call).
