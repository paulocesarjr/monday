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

## Versioning

Claude Code caches installed plugins **per version**. If you change anything under `plugins/monday/` without bumping `version` in `plugins/monday/.claude-plugin/plugin.json`, users who update will keep the old copy.

Every PR that changes the plugin must bump the version, following [SemVer](https://semver.org):

| Change | Example |
|---|---|
| Bug fix, prompt tweak, docs inside the plugin | `0.2.0` → `0.2.1` |
| New command, integration or feature | `0.2.0` → `0.3.0` |
| Breaking change (renamed command, profile format change) | `0.x` → `1.0.0` |

Changes only to repo docs (`README.md`, `CONTRIBUTING.md`, `docs/`) don't need a bump.

To test an update locally after a bump:

```
/plugin marketplace update monday
/plugin uninstall monday@monday
/plugin install monday@monday
/reload-plugins
```

## Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org): `feat:`, `fix:`, `docs:`, `chore:`, `refactor:`...

## Rules

- Never commit credentials, tokens or client secrets.
- Keep the "read freely, write carefully" rule in every command that can change state.
- One feature per PR, with a short description of how you tested it.
