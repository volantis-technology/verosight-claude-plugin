---
name: chat
description: Ask Verosight's AI assistant any social media intelligence question. Usage - /verosight:chat <question>
user-invocable: true
allowed-tools: Bash(curl *)
---

# AI Chat

Ask Verosight's AI assistant any social media intelligence question. The AI has access to all Verosight tools and can search, analyze, and reason over social media data.

User's question: $ARGUMENTS

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Send the user's question to the chat endpoint.
3. Stream and present the response.

## API Call

```bash
curl -sN "https://api.verosight.com/v1/chat" \
  -H "X-API-Key: $VEROSIGHT_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"message": "USER_QUESTION"}'
```

The response is SSE (Server-Sent Events). Parse the stream:
- `event: conversation_id` — the conversation ID for follow-ups
- `event: tool_status` — shows which tools the AI is using
- `event: content_block_delta` — streaming text response
- `event: done` — response complete

For follow-up questions in the same conversation, include the conversation_id:
```bash
curl -sN "https://api.verosight.com/v1/chat" \
  -H "X-API-Key: $VEROSIGHT_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"message": "FOLLOW_UP", "conversation_id": "CONV_ID"}'
```

Parse the user's request:
- "what's trending about AI right now" → message: "what's trending about AI right now"
- "analyze Nike vs Adidas on instagram" → message: "analyze Nike vs Adidas engagement on Instagram"
- Any natural language question about social media → pass directly

## Output Format

Collect all `content_block_delta` events and present the full response. If the AI used tools, briefly note which tools were invoked (from `tool_status` events).

Show credits used (20 per call).
