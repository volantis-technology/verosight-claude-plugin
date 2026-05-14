---
description: Check your Verosight API credit balance and usage.
allowed-tools: Bash(curl *)
---

# Credit Balance

Check the user's Verosight API credit balance and rate limit status.

## API Call

```bash
curl -s "https://api.verosight.com/v1/account/balance" \
  -H "X-API-Key: ${user_config.api_key}"
```

## Output Format

Show: credits remaining, credits used today, account tier, rate limit, rate limit remaining.
