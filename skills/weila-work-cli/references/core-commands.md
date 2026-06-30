---
name: weila-work-cli-commands
description: Global options and full command overview for weila-work-cli.
---

# CLI Commands Overview

`weila-work-cli` is built with `cac` and exposes namespaced commands under `auth:`, `org:`, `address:`, and `group:`.

## Global Options

Every command accepts these options:

```bash
weila-work-cli <command> [options]
  --profile <name>   Config profile (default: default)
  --base-url <url>   API base URL (default: https://voiswork.cn/v2)
  --app-id <id>      App ID
  --app-key <key>    App Key
  --token <token>    Access token (in-memory auth, skips profile login)
  --json             Output raw JSON (default)
  --debug            Print debug information
```

## Command Overview

Use `weila-work-cli --help` to show all commands. Use `weila-work-cli <command> --help` for command-specific examples.

### Auth

| Command | Purpose |
|---------|---------|
| `weila-work-cli auth:login` | Login with account and password |
| `weila-work-cli auth:set-token` | Store an access token directly without logging in |
| `weila-work-cli auth:whoami` | Get current user info |

### Org

| Command | Purpose |
|---------|---------|
| `weila-work-cli org:get` | Get current organization |
| `weila-work-cli org:vip` | Get current organization VIP info |
| `weila-work-cli org:create` | Create an organization |
| `weila-work-cli org:change` | Update organization name/avatar |

### Address Book

| Command | Purpose |
|---------|---------|
| `weila-work-cli address:dept-list` | List managed departments |
| `weila-work-cli address:dept-all` | List all departments (flat) |
| `weila-work-cli address:dept-tree` | List all departments for tree widgets |
| `weila-work-cli address:member-list` | Paginated member list across organization |
| `weila-work-cli address:dept-member-list` | Paginated members of a department |
| `weila-work-cli address:dept-members` | Get all members of a department |
| `weila-work-cli address:member` | Get a single member |
| `weila-work-cli address:member-create` | Create a new organization member |
| `weila-work-cli address:member-change` | Update an existing member |
| `weila-work-cli address:member-state` | Enable or disable a member account |
| `weila-work-cli address:member-delete` | Delete a member |
| `weila-work-cli address:dept-members-add` | Add existing members to a department |
| `weila-work-cli address:dept-create` | Create a department |
| `weila-work-cli address:dept-change` | Rename a department |
| `weila-work-cli address:dept-delete` | Delete a department |
| `weila-work-cli address:device-add` | Add a device member |
| `weila-work-cli address:member-reset-password` | Reset a member password |

### Groups

| Command | Purpose |
|---------|---------|
| `weila-work-cli group:list` | List groups you manage |
| `weila-work-cli group:get` | Get a group by ID |
| `weila-work-cli group:members` | List all members of a group |
| `weila-work-cli group:member-list` | Paginated group member list |
| `weila-work-cli group:create` | Create a group |
| `weila-work-cli group:change` | Update a group |
| `weila-work-cli group:delete` | Delete a group |
| `weila-work-cli group:members-add` | Add members to a group |
| `weila-work-cli group:member-delete` | Remove a member from a group |

## Key Points

- `--json` is the default output format; all responses are printed as raw JSON.
- Use `--debug` to print debug information for troubleshooting.
- Profile config and tokens are persisted under `~/.config/weila-work-cli/profiles/<profile>/`.
- Commands that accept `--md5` skip automatic MD5 hashing of the provided password.
- Boolean-like flags (`--is-dept-admin`, `--loc-share`, `--track`, `--burst-mode`) accept `true`, `false`, `0`, or `1`.
- Org/address/group commands require an access token; obtain it via `auth:login`, `auth:set-token`, or the per-command global `--token` option — any of the three works.

<!-- Source references: packages/cli/src/cli.ts, packages/cli/src/commands/_shared.ts, packages/cli/src/commands/auth.ts, packages/cli/src/commands/org.ts, packages/cli/src/commands/address.ts, packages/cli/src/commands/group.ts -->
