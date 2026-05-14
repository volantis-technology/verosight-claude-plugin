---
description: Get AI-powered recommendations based on social media buzz. Categories include products, movies, books, software, games, travel, skills, content, marketing, problems. Use when the user asks for recommendations.
allowed-tools: Bash(curl *)
---

# AI Recommendations

Get AI-generated recommendations based on social media conversations.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/recommendations/CATEGORY?days=7" \
  -H "X-API-Key: ${user_config.api_key}"
```

**Categories:** products, movies, books, software, games, travel, skills, content, marketing, problems

**Parameters:**
- `query` — optional topic to focus recommendations
- `days` — period 1-90 (default 7)
- `platform` — filter source data by platform

Parse the user's request:
- "recommend products trending in tech" → category=products, query=tech
- "what movies are people talking about" → category=movies
- "software recommendations for developers" → category=software, query=developers
- "what content should I create about AI" → category=content, query=AI
- "marketing ideas for fashion brand" → category=marketing, query=fashion

## Output Format

For each recommendation: name/title, why it's recommended (social signals), engagement data, source platforms.

Show credits used (15 per call).
