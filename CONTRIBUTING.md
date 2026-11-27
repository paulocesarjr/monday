# Contributing to Monday

Thanks for helping! 🎉

## Project layout

```
.claude-plugin/marketplace.json   # makes this repo installable as a plugin marketplace
plugins/monday/
  .claude-plugin/plugin.json      # plugin manifest (name, version, ...)
  .mcp.json                       # bundled MCP servers (integrations)
  skills/monday/SKILL.md          # Monday's persona and ground rules
  commands/*.md                   # slash commands (/monday:<name>)
docs/integrations.md              # setup guide per integration
```

## Developing locally

```bash
git clone https://github.com/paulocesarjr/monday
cd monday
claude
```

Inside Claude Code:

```
/plugin marketplace add ./
/plugin install monday@monday
```

After editing files, reinstall or restart Claude Code to pick up changes. Run `claude plugin validate .` before opening a PR.

## Adding a command

Create `plugins/monday/commands/<name>.md` with a `description` in the frontmatter. Tell it to use the `monday` skill persona and to **ask before any write action**. Look at `morning.md` for an example.

## Adding an integration

1. Prefer an **official remote MCP server** with OAuth (no secrets in the repo).
2. If it's universally useful, add it to `plugins/monday/.mcp.json`. If it needs per-user setup (API apps, keys), document it in `docs/integrations.md` instead.
3. Update the integrations table in `README.md` and in `skills/monday/SKILL.md`.

## Rules

- Never commit credentials, tokens or client secrets.
- Keep the "read freely, write carefully" rule in every command that can change state.
- One feature per PR, with a short description of how you tested it.
