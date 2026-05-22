---
description: Get a single social media post by its numeric ID. Use when the user references a specific post ID or wants full details of one post.
allowed-tools: Bash(curl *)
---

# Get Post

Get a single social media post by its numeric ID.

User's request: $ARGUMENTS

## API Call

```bash
curl -s "https://api.verosight.com/v1/posts/POST_ID" \
  -H "X-API-Key: ${user_config.api_key}"
```

Parse the user's request:
- "show me post 12345" -> POST_ID=12345
- "get details for post id 98765" -> POST_ID=98765

## Output Format

Full post details: platform, author, content, engagement (likes/comments/shares/views), media type, URL, posted date.

Show credits used (2 per call).
