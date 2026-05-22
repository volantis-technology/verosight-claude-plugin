---
description: Semantic similarity search across posts, comments, and profiles using vector embeddings. Use when the user wants meaning-based search rather than exact keyword matching. Supports multi-query via pipe separator.
allowed-tools: Bash(curl *)
---

# Semantic Search

Search across posts, comments, and profiles using vector embeddings for meaning-based relevance.

User's query: $ARGUMENTS

## API Call

```bash
curl -s -X POST "https://api.verosight.com/v1/search" \
  -H "X-API-Key: ${user_config.api_key}" \
  -H "Content-Type: application/json" \
  -d '{"query": "QUERY", "limit": 20}'
```

**Request body:**
- `query` — required, search text. Use `" | "` pipe separator for multiple queries in one call
- `limit` — max results 1-100 (default 20)
- `filters.platforms` — array of platforms to filter
- `filters.exclude_profiles` — array of profile names to exclude
- `filters.exclude_keywords` — array of keywords to exclude

**Multi-query example:**
```json
{
  "queries": [
    {"query": "AI regulation", "limit": 10},
    {"query": "climate policy", "limit": 10}
  ]
}
```

Parse the user's request:
- "search for posts about AI ethics" -> query=AI ethics
- "semantic search climate change on instagram" -> query=climate change, filters.platforms=["instagram"]
- "find posts similar to democratic reform" -> query=democratic reform

## Output Format

For each result: type (post/comment/profile), platform, author, content (~200 chars), similarity score, engagement, URL.

Show credits used (3 per call).
