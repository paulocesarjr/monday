# Integrations

Monday uses [MCP servers](https://modelcontextprotocol.io) to talk to each service. Authentication happens through OAuth when you run `/mcp` in Claude Code.

## GitHub (chosen during setup)

Official remote server: `https://api.githubcopilot.com/mcp`. In Claude Code it authenticates with a token.
`/monday:setup` registers it only if you pick GitHub. To do it by hand, with the GitHub CLI logged in:

```bash
claude mcp add -s user --transport http github https://api.githubcopilot.com/mcp \
  -H "Authorization: Bearer $(gh auth token)"
```

Or create a [fine-grained Personal Access Token](https://github.com/settings/personal-access-tokens) and use it in place of `$(gh auth token)`. Never paste tokens into the chat.
Docs: https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/set-up-the-github-mcp-server

## GitLab (chosen during setup)

GitLab's built-in MCP server at `<your-gitlab>/api/v4/mcp`, which works for gitlab.com and self-hosted instances. It uses OAuth.

```bash
claude mcp add -s user --transport http gitlab https://gitlab.com/api/v4/mcp
```

Restart Claude Code, run `/mcp`, pick **gitlab** and sign in. Availability depends on your GitLab version and tier, and on self-hosted instances an admin may need to enable it (a 403 usually means it's turned off).
Docs: https://docs.gitlab.com/user/model_context_protocol/mcp_server/

## Jira (bundled)

Atlassian's official remote MCP server: `https://mcp.atlassian.com/v2/mcp`.
Run `/mcp`, pick **atlassian** and sign in. Your Atlassian admin may need to allow the integration.
Docs: https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/

## Notion (bundled)

Notion's official remote MCP server: `https://mcp.notion.com/mcp`.
Run `/mcp`, pick **notion** and sign in. Choose which pages and workspaces Monday can see.
Docs: https://developers.notion.com/guides/mcp/get-started-with-mcp

## Slack (bundled)

Slack's official remote MCP server: `https://mcp.slack.com/mcp`, using the same OAuth configuration as Slack's own Claude plugin.
Run `/mcp`, pick **slack** and sign in. Your **Slack workspace admin must approve MCP integration** before you can authenticate.

If you also installed Slack's official plugin (`/plugin install slack`), keep only one of the two so the tools aren't duplicated.

**About the `clientId` in `.mcp.json`:** it isn't a leaked credential. OAuth client IDs are public by design. This is a public client (PKCE, no client secret), and Slack only redirects to `http://localhost:3118` on your own machine, so the ID alone grants no access. It belongs to the Slack app that Slack's official Claude plugin uses, which is why the sign-in screen shows that app and not "Monday". If Slack rotates it, we'll update it here.
Docs: https://docs.slack.dev/ai/slack-mcp-server/connect-to-claude

## Outlook / Microsoft 365 (chosen during setup)

Monday uses the community [`@softeria/ms-365-mcp-server`](https://github.com/Softeria/ms-365-mcp-server) (MIT), which talks to Microsoft Graph and ships with a built-in app, so you don't need to register one in Entra ID. It runs locally through `npx` (Node.js 20+), and tokens are cached in your OS keychain. Monday enables only the `outlook` preset (mail, calendar and contacts).

`/monday:setup` registers it only if you say you use Outlook. To do it by hand:

```bash
# Work or school account (Microsoft 365)
claude mcp add -s user ms365 -- npx -y @softeria/ms-365-mcp-server --org-mode --preset outlook

# Personal account (Outlook.com / Hotmail)
claude mcp add -s user -e MS365_MCP_TENANT_ID=consumers ms365 -- npx -y @softeria/ms-365-mcp-server --preset outlook
```

Add `--read-only` if you want Monday to only read (no drafts, sending or calendar changes; focus mode won't be able to block time).
On Windows, wrap the command: `-- cmd /c "npx -y @softeria/ms-365-mcp-server --org-mode --preset outlook"`.

Restart Claude Code, then ask Monday to sign in to Outlook. It calls the server's `login` tool, which shows a URL and a code (device code flow). Open the URL, type the code and sign in (with your work email for work accounts), then tell Monday "pronto" so it can confirm. The code expires in about 15 minutes; just ask for a new one. Registering the server doesn't sign you in, so if Monday ever says Outlook needs a sign-in (for example after the session expires), it's this same step again. You can also sign in from a terminal: `npx -y @softeria/ms-365-mcp-server --login` (add the same `--org-mode` or `MS365_MCP_TENANT_ID` you used above).

**Company tenants:** many organizations block user consent for third-party apps. If sign-in says an admin needs to approve it, ask IT. `npx -y @softeria/ms-365-mcp-server --org-mode --preset outlook --list-permissions` lists the Graph permissions to send them.

**Official alternatives:** Microsoft's own Work IQ Mail/Calendar MCP servers (Agent 365) need a Microsoft 365 Copilot license and a tenant admin to enable them. On Claude Team/Enterprise plans, an admin can also enable the Microsoft 365 connector in claude.ai, and its tools then show up in Claude Code. Monday works with any of them; keep only one connected so the tools aren't duplicated.

## Spotify (optional, TODO)

Uses the Spotify Web API. Each user creates their own app at https://developer.spotify.com. Controlling playback requires **Spotify Premium**.
We haven't picked a recommended MCP server yet. Contributions are welcome!
