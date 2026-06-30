---
name: weila-work-cli-org
description: Organization commands for weila-work-cli.
---

# Org Commands

Org commands read and manage the current organization.

## `org:get`

Get current organization info.

```bash
weila-work-cli org:get
```

Alias: `org`

## `org:vip`

Get current organization VIP info.

```bash
weila-work-cli org:vip
```

## `org:create`

Create a new organization.

### Options

| Option | Description |
|--------|-------------|
| `--name <name>` | Organization name |
| `--avatar <url>` | Avatar URL |

### Example

```bash
weila-work-cli org:create --name "My Org"
```

## `org:change`

Update organization name/avatar.

### Options

| Option | Description |
|--------|-------------|
| `--name <name>` | Organization name |
| `--avatar <url>` | Avatar URL |

### Example

```bash
weila-work-cli org:change --name "New Name"
```

## Key Points

- `org:get` returns the organization associated with the authenticated user.
- `org:create` requires at least `--name`.
- `org:change` only updates the fields that are provided.

<!-- Source references: packages/cli/src/commands/org.ts -->
