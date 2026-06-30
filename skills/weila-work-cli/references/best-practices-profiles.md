---
name: weila-work-cli-profiles
description: Config profiles, token persistence, and auth tips for weila-work-cli.
---

# Profiles and Auth Best Practices

## Profiles

Use `--profile <name>` to isolate config and tokens for different environments or accounts. The default profile is `default`.

```bash
weila-work-cli auth:login --account 70009790 --password 123456 --profile prod
weila-work-cli org:get --profile prod
```

## Config and Token Persistence

Profile config and tokens are persisted under:

```
~/.config/weila-work-cli/profiles/<profile>/
```

The profile directory contains:

- `config.json` - Profile-specific base URL, app ID, and app key.
- Token storage (via unstorage) - Access token written by `auth:login`.

## Base URL and App Credentials

Global options can override profile values per command:

```bash
weila-work-cli org:get --base-url https://voiswork.cn/v2 --app-id 102065 --app-key 3c227f2cbc2084ebdd9617fd283c42c7
```

Resolution order:

1. Command-line option (`--base-url`, `--app-id`, `--app-key`)
2. Profile config (`~/.config/weila-work-cli/profiles/<profile>/config.json`)
3. Built-in defaults (`https://voiswork.cn/v2`, app ID `102065`, app key `3c227f2cbc2084ebdd9617fd283c42c7`)

## Login First

Most commands require an authenticated API client. Run `auth:login` before calling org, address, or group commands.

```bash
weila-work-cli auth:login --account 70009790 --password 123456
weila-work-cli address:member-list --key "Alice"
```

## Key Points

- Each profile has its own token; switching profiles requires logging in again if no token is stored.
- Use `--debug` to inspect which base URL and profile are being used.
- Keep profile config files secure; they contain app credentials and tokens.

<!-- Source references: packages/cli/src/config.ts, packages/cli/src/client.ts, packages/cli/src/commands/_shared.ts, packages/cli/src/commands/auth.ts -->
