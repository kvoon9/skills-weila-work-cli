---
name: weila-work-cli-auth
description: Auth commands for weila-work-cli.
---

# Auth Commands

Auth commands handle login and current user info. Login must be performed before other commands that require an access token.

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

## `auth:whoami`

Get current user info using the stored token.

```bash
weila-work-cli auth:whoami
```

## Key Points

- `auth:login` stores the returned `access_token` in the active profile storage.
- Omitting `--md5` causes the CLI to hash `--password` with MD5 before sending it.
- Use `--profile` to log in to a different config profile.

<!-- Source references: packages/cli/src/commands/auth.ts -->
