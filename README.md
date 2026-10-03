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

## Verify configuration changes

Run these checks from the repository root. For a quick JSON syntax check with Node.js:

```sh
node -e "JSON.parse(require('node:fs').readFileSync('renovate.json', 'utf8'))"
```

For Renovate option validation, install a Renovate distribution using the Node.js version it supports, then run its standalone validator:

```sh
renovate-config-validator renovate.json
```

Passing a filename validates global self-hosted configuration, matching this repository's [scheduled workflow](.github/workflows/renovate.yml), which reads `renovate.json` and its repository list. See the [validator documentation](https://docs.renovatebot.com/config-validation/) for installation via npm and flags. JSON parsing alone does not check Renovate options or preset resolution; record the validator version and any warnings or unavailable validation separately. This repository has no test, build, or pull-request validation workflow.

The scheduled workflow and its manual dispatch run Renovate against the listed GitHub repositories using `RENOVATE_TOKEN`; they can create and merge dependency pull requests. Do not trigger that workflow as a configuration test. The standalone validator does not run the update bot, and these local checks do not prove a scheduled provider run.
