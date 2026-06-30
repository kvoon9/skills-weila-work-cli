---
name: weila-work-cli-install
description: Install the weila-work-cli binary and its agent skill.
---

# Install the weila-work-cli

## Agent skill

Add the project skill to your agent:

```bash
npx skills add kvoon9/weila-work
```

## CLI from npm

Install globally:

```bash
npm -g install weila-work-cli
```

Or run once with `npx`:

```bash
npx weila-work-cli --help
```

## Verify

```bash
weila-work-cli --version
weila-work-cli --help
```

## Key Points

- The binary is registered as `weila-work-cli` in `packages/cli/package.json`.
- Current published version is `0.0.2`.
- When running from source, build first: `pnpm --filter weila-work-cli build`.
- The CLI persists profile config and tokens under `~/.config/weila-work-cli/profiles/<profile>/`.
- Most commands require an access token; obtain it via `auth:login`, `auth:set-token`, or the per-command `--token` option.

<!-- Source references: packages/cli/package.json, packages/cli/README.md -->
