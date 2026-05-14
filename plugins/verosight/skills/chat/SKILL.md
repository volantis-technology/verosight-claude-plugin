---
description: Ask Verosight's AI assistant any social media intelligence question. The AI has access to all Verosight tools. Use when the user has a complex or open-ended social media question.
allowed-tools: Bash(curl *)
---

# AI Chat

Ask Verosight's AI assistant any social media intelligence question.

User's question: $ARGUMENTS

## API Call

```bash
curl -sN "https://api.verosight.com/v1/chat" \
  -H "X-API-Key: ${user_config.api_key}" \
  -H "Content-Type: application/json" \
  -d '{"message": "USER_QUESTION"}'
```

The response is SSE (Server-Sent Events). Parse the stream:
- `event: conversation_id` — the conversation ID for follow-ups
- `event: tool_status` — shows which tools the AI is using
- `event: content_block_delta` — streaming text response
- `event: done` — response complete

For follow-up questions, include the conversation_id:
```bash
curl -sN "https://api.verosight.com/v1/chat" \
  -H "X-API-Key: ${user_config.api_key}" \
  -H "Content-Type: application/json" \
  -d '{"message": "FOLLOW_UP", "conversation_id": "CONV_ID"}'
```

## Output Format

Collect all `content_block_delta` events and present the full response. Note which tools the AI invoked.

Show credits used (20 per call).
