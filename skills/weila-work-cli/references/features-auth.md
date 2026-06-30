---
name: weila-work-cli-auth
description: Auth commands for weila-work-cli.
---

# Auth Commands

Auth commands establish the access token that org, address, and group commands require. You can authenticate with **account + password** (`auth:login`), store a token you already have (`auth:set-token`), or pass a token per-command with the global `--token` option. None of these is preferred over the others — pick whichever fits your context.

## `auth:login`

Login with account and password. The password is MD5-hashed automatically unless `--md5` is provided.

### Options

| Option | Description |
|--------|-------------|
| `--account <account>` | Account number |
| `--password <password>` | Password (plain text; will be MD5 hashed) |
| `--md5` | Password is already MD5 hashed |

### Examples

```bash
# Plain password (automatically hashed)
weila-work-cli auth:login --account 70009790 --password 123456

# Already-hashed password
weila-work-cli auth:login --account 70009790 --password e10adc3949ba59abbe56e057f20f883e --md5
```

## `auth:set-token`

Store an access token directly into the active profile, without account/password. Use this when you already hold a valid access token (e.g. obtained from a logged-in session).

### Options

| Option | Description |
|--------|-------------|
| `--token <token>` | Access token to persist into the profile |

### Examples

```bash
weila-work-cli auth:set-token --token <access-token>
```

## Global `--token` option

Every command also accepts the global `--token <token>` option. When provided, the CLI uses an in-memory token for that single invocation and **skips profile login entirely** — nothing is written to disk. This is the right fit for one-off calls or when a host process passes a token in (e.g. the Weila Work app forwards the logged-in session token).

```bash
weila-work-cli org:get --token <access-token>
weila-work-cli address:member-list --key "Alice" --token <access-token>
```

## `auth:whoami`

Get current user info using the stored token.

```bash
weila-work-cli auth:whoami
```

## Key Points

- Org/address/group commands need an access token; obtain it via `auth:login`, `auth:set-token`, or the per-command `--token` option — all are valid.
- `auth:login` stores the returned `access_token` in the active profile storage.
- `auth:set-token` persists a supplied token to the active profile; the global `--token` uses in-memory auth and does not touch the profile.
- Omitting `--md5` causes the CLI to hash `--password` with MD5 before sending it.
- Use `--profile` to log in to (or store a token for) a different config profile.

<!-- Source references: packages/cli/src/commands/auth.ts, packages/cli/src/commands/_shared.ts, packages/cli/src/client.ts -->
