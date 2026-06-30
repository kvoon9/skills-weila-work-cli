---
name: weila-work-cli-group
description: Group management commands for weila-work-cli.
---

# Group Commands

Group commands are grouped under the `group:` namespace. They manage groups and group membership.

## `group:list`

List groups you manage.

| Option | Description |
|--------|-------------|
| `--page <page>` | Page number (default: 1) |
| `--size <size>` | Page size (default: 20) |

```bash
weila-work-cli group:list --page 1 --size 20
```

## `group:get`

Get a group by ID.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |

```bash
weila-work-cli group:get --id 123
```

## `group:members`

List all members of a group.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |

```bash
weila-work-cli group:members --id 123
```

## `group:member-list`

Paginated group member list.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |
| `--page <page>` | Page number (default: 1) |
| `--size <size>` | Page size (default: 20) |

```bash
weila-work-cli group:member-list --id 123 --page 1 --size 20
```

## `group:create`

Create a group.

| Option | Description |
|--------|-------------|
| `--name <name>` | Group name |
| `--dept-id <id>` | Department ID |
| `--burst-mode <mode>` | Burst mode: 0 or 1 |
| `--avatar <url>` | Avatar URL |

```bash
weila-work-cli group:create --name "Ops" --burst-mode 1
```

## `group:change`

Update a group.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |
| `--name <name>` | Group name |
| `--burst-mode <mode>` | Burst mode: 0 or 1 |
| `--avatar <url>` | Avatar URL |

```bash
weila-work-cli group:change --id 123 --name "New Name"
```

## `group:delete`

Delete a group.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |

```bash
weila-work-cli group:delete --id 123
```

## `group:members-add`

Add members to a group.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |
| `--user-ids <ids>` | User IDs (comma separated) |

```bash
weila-work-cli group:members-add --id 123 --user-ids 1,2,3
```

## `group:member-delete`

Remove a member from a group.

| Option | Description |
|--------|-------------|
| `--id <id>` | Group ID |
| `--user-id <userId>` | User ID |

```bash
weila-work-cli group:member-delete --id 123 --user-id 456
```

## Key Points

- `--burst-mode` accepts `0` or `1`.
- `--user-ids` is parsed as a comma-separated list of numbers.
- `group:members` returns all members; `group:member-list` returns a paginated result.

<!-- Source references: packages/cli/src/commands/group.ts -->
