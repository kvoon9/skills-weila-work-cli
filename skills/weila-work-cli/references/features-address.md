---
name: weila-work-cli-address
description: Address book department and member commands for weila-work-cli.
---

# Address Book Commands

Address book commands are grouped under the `address:` namespace. They manage departments and organization members.

## Departments

### `address:dept-list`

List managed departments.

| Option | Description |
|--------|-------------|
| `--dept-id <id>` | Scope to a specific department |

```bash
weila-work-cli address:dept-list
weila-work-cli address:dept-list --dept-id 5
```

### `address:dept-all`

List all departments as a flat list.

```bash
weila-work-cli address:dept-all
```

### `address:dept-tree`

List all departments formatted for tree widgets.

```bash
weila-work-cli address:dept-tree
```

### `address:dept-create`

Create a department.

| Option | Description |
|--------|-------------|
| `--name <name>` | Department name |

```bash
weila-work-cli address:dept-create --name "Sales"
```

### `address:dept-change`

Rename a department.

| Option | Description |
|--------|-------------|
| `--dept-id <id>` | Department ID |
| `--name <name>` | New name |

```bash
weila-work-cli address:dept-change --dept-id 5 --name "New Name"
```

### `address:dept-delete`

Delete a department.

| Option | Description |
|--------|-------------|
| `--dept-id <id>` | Department ID |

```bash
weila-work-cli address:dept-delete --dept-id 5
```

### `address:dept-members-add`

Add existing members to a department.

| Option | Description |
|--------|-------------|
| `--dept-id <id>` | Department ID |
| `--user-ids <ids>` | User IDs (comma separated) |

```bash
weila-work-cli address:dept-members-add --dept-id 5 --user-ids 1,2,3
```

## Members

### `address:member-list`

Paginated member list across the organization.

| Option | Description |
|--------|-------------|
| `--key <key>` | Search keyword |
| `--member-types <types>` | Member types (comma separated) |
| `--dept-ids <ids>` | Department IDs (comma separated) |
| `--page <page>` | Page number (default: 1) |
| `--size <size>` | Page size (default: 20) |

```bash
weila-work-cli address:member-list --key zhang --dept-ids 1,2
```

### `address:dept-member-list`

Paginated members of a department.

| Option | Description |
|--------|-------------|
| `--dept-id <id>` | Department ID |
| `--key <key>` | Search keyword |
| `--member-types <types>` | Member types (comma separated) |
| `--page <page>` | Page number (default: 1) |
| `--size <size>` | Page size (default: 20) |

```bash
weila-work-cli address:dept-member-list --dept-id 5
```

### `address:dept-members`

Get all members of a department.

| Option | Description |
|--------|-------------|
| `--dept-id <id>` | Department ID |

```bash
weila-work-cli address:dept-members --dept-id 5
```

### `address:member`

Get a single member.

| Option | Description |
|--------|-------------|
| `--id <id>` | Member ID |

```bash
weila-work-cli address:member --id 123
```

### `address:member-create`

Create a new organization member.

| Option | Description |
|--------|-------------|
| `--name <name>` | Member name |
| `--phone <phone>` | Phone number |
| `--password <password>` | Password (plain text; will be MD5 hashed) |
| `--md5` | Password is already MD5 hashed |
| `--job-num <num>` | Job number |
| `--dept-id <id>` | Department ID |
| `--sex <sex>` | Sex: 0 female, 1 male |
| `--avatar <url>` | Avatar URL |
| `--is-dept-admin <enabled>` | Is department admin (true/false/0/1) |
| `--loc-share <enabled>` | Location sharing (true/false/0/1) |
| `--track <enabled>` | Track enabled (true/false/0/1) |

```bash
weila-work-cli address:member-create --name "John" --password 123456 --dept-id 5
```

### `address:member-change`

Update an existing member.

| Option | Description |
|--------|-------------|
| `--user-id <id>` | Member user ID |
| `--name <name>` | Member name |
| `--job-num <num>` | Job number |
| `--dept-id <id>` | Department ID |
| `--sex <sex>` | Sex: 0 female, 1 male |
| `--avatar <url>` | Avatar URL |
| `--phone <phone>` | Phone number |
| `--is-dept-admin <enabled>` | Is department admin (true/false/0/1) |
| `--loc-share <enabled>` | Location sharing (true/false/0/1) |
| `--track <enabled>` | Track enabled (true/false/0/1) |

```bash
weila-work-cli address:member-change --user-id 123 --name "New Name"
```

### `address:member-state`

Enable or disable a member account.

| Option | Description |
|--------|-------------|
| `--user-id <id>` | Member user ID |
| `--state <state>` | State: 0 disabled, 1 enabled |

```bash
weila-work-cli address:member-state --user-id 123 --state 1
```

### `address:member-delete`

Delete a member.

| Option | Description |
|--------|-------------|
| `--user-id <id>` | Member user ID |

```bash
weila-work-cli address:member-delete --user-id 123
```

### `address:member-reset-password`

Reset a member password.

| Option | Description |
|--------|-------------|
| `--user-id <id>` | Member user ID |
| `--password <password>` | New password (plain text; will be MD5 hashed) |
| `--md5` | Password is already MD5 hashed |

```bash
weila-work-cli address:member-reset-password --user-id 123 --password xxx
```

## Device Members

### `address:device-add`

Add a device member.

| Option | Description |
|--------|-------------|
| `--name <name>` | Device name |
| `--verifycode <code>` | Device verify code |
| `--job-num <num>` | Job number |
| `--dept-id <id>` | Department ID |
| `--sex <sex>` | Sex |
| `--avatar <url>` | Avatar URL |
| `--phone <phone>` | Phone number |
| `--loc-share <enabled>` | Location sharing (true/false/0/1) |
| `--track <enabled>` | Track enabled (true/false/0/1) |

```bash
weila-work-cli address:device-add --name "Device 1" --verifycode xxx
```

## Boolean and Number Parsing

- `--sex` accepts `0` (female) or `1` (male).
- `--is-dept-admin`, `--loc-share`, and `--track` accept `true`, `false`, `0`, or `1`.
- Comma-separated lists (`--member-types`, `--dept-ids`, `--user-ids`) are parsed into number arrays.

<!-- Source references: packages/cli/src/commands/address.ts -->
