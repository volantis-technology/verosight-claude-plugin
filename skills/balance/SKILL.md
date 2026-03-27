---
name: balance
description: Check your Verosight API credit balance and usage. Usage - /verosight:balance
user-invocable: true
allowed-tools: Bash(curl *)
---

# Credit Balance

Check the user's Verosight API credit balance and rate limit status.

## Instructions

1. Use the `VEROSIGHT_API_KEY` environment variable.
2. Call the balance endpoint.
3. Present the information clearly.

## API Call

```bash
curl -s "https://api.verosight.com/v1/account/balance" \
  -H "X-API-Key: $VEROSIGHT_API_KEY"
```

## Output Format

Show:
- Credits remaining
- Credits used today
- Account tier
- Rate limit (requests/minute)
- Rate limit remaining

If the API key is not set, tell the user to run `/verosight:setup` first.
