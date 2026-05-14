---
name: recommendations
description: Get AI-powered recommendations based on social media buzz. Usage - /verosight:recommendations <category> [query]
user-invocable: true
allowed-tools: Bash(curl *)
---

# AI Recommendations

Get AI-generated recommendations based on social media conversations.

User's request: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Parse the recommendation category and optional topic from the request.
3. Call the recommendations endpoint.
4. Present recommendations clearly with reasoning.

## API Call

```bash
curl -s "https://api.verosight.com/v1/recommendations/CATEGORY?days=7" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

**Categories:** products, movies, books, software, games, travel, skills, content, marketing, problems

**Parameters:**
- `query` — optional topic to focus recommendations (e.g. "AI tools", "Indonesia travel")
- `days` — period 1-90 (default 7)
- `platform` — filter source data by platform

Parse the user's request:
- "recommend products trending in tech" → category=products, query=tech
- "what movies are people talking about" → category=movies
- "software recommendations for developers" → category=software, query=developers
- "travel recommendations for Indonesia" → category=travel, query=Indonesia
- "what content should I create about AI" → category=content, query=AI
- "marketing ideas for fashion brand" → category=marketing, query=fashion

## Output Format

For each recommendation:
- Name/title
- Why it's recommended (based on social signals)
- Relevant engagement data
- Source platforms

Show credits used (15 per call).
