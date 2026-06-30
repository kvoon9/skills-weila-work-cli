---
name: weila-work-cli
description: Use the weila-work-cli to manage Weila Work (微喇企业管理台; Weila = 微喇) auth, org, address book, and groups through the management APIs. Use it when the user mentions 微喇 / 微喇企业管理台 / Weila / Weila Work.
metadata:
  author: kvoon
  version: "0.0.4"
  source: packages/cli
---

> The skill is based on `weila-work-cli` v0.0.4, generated from `packages/cli`.

`weila-work-cli` is the command-line interface for Weila Work management APIs. **Weila** is **微喇** in Chinese, and **Weila Work** is **微喇企业管理台** (its enterprise management console). It wraps the HTTP endpoints used by `weila-work/packages/web` and exposes commands for authentication, organization info, address book departments/members, and group management. Real-time / websocket SDK interfaces are not exposed.

It is published on npm as [`weila-work-cli`](https://www.npmjs.com/package/weila-work-cli). Install it globally and invoke the `weila-work-cli` binary, or run it ad-hoc without installing:

```bash
# Global install, then run
npm -g install weila-work-cli
weila-work-cli --help

# Or run once via npx
npx weila-work-cli --help
```

Log in once before using the org/address/group commands; see [core-install](references/core-install.md) and [features-auth](references/features-auth.md) for details.

## Core References

| Topic | Description | Reference |
|-------|-------------|-----------|
| Install CLI | Install and verify the `weila-work-cli` binary | [core-install](references/core-install.md) |
| Commands | Global options and full command overview | [core-commands](references/core-commands.md) |

## Features

### Auth

| Topic | Description | Reference |
|-------|-------------|-----------|
| Auth Commands | Login and current user info | [features-auth](references/features-auth.md) |

### Org

| Topic | Description | Reference |
|-------|-------------|-----------|
| Org Commands | Get, create, and update organization info | [features-org](references/features-org.md) |

### Address Book

| Topic | Description | Reference |
|-------|-------------|-----------|
| Address Commands | Manage departments and members | [features-address](references/features-address.md) |

### Groups

| Topic | Description | Reference |
|-------|-------------|-----------|
| Group Commands | Manage groups and group members | [features-group](references/features-group.md) |

## Best Practices

| Topic | Description | Reference |
|-------|-------------|-----------|
| Profiles and Auth | Config profiles, token persistence, and base URL / app credential usage | [best-practices-profiles](references/best-practices-profiles.md) |

<!-- Source references: packages/cli/package.json, packages/cli/README.md, packages/cli/src/cli.ts, packages/cli/src/client.ts, packages/cli/src/config.ts, packages/cli/src/commands/_shared.ts, packages/cli/src/commands/auth.ts, packages/cli/src/commands/org.ts, packages/cli/src/commands/address.ts, packages/cli/src/commands/group.ts -->
