# Renovate Config

Shared [Renovate](https://github.com/renovatebot/renovate) configuration for the saagpatel portfolio.

## Usage

Add this to any repo's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>saagpatel/renovate-config"]
}
```

## Behavior

- Patch and minor updates: auto-merged (grouped into one PR per repo)
- Major updates: PR opened, requires manual review
- Dev dependencies: always auto-merged
- Schedule: Monday mornings before 8am ET
- Rate limit: max 3 concurrent PRs, 2 per hour
- Security alerts: always opened immediately regardless of schedule
