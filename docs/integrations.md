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
Docs: https://docs.slack.dev/ai/slack-mcp-server/connect-to-claude

## Outlook Calendar (optional, TODO)

Uses Microsoft Graph. Requires an app registration in Microsoft Entra ID (Azure), and many company tenants block user consent, so check with IT.
We haven't picked a recommended MCP server yet. Contributions are welcome!

## Spotify (optional, TODO)

Uses the Spotify Web API. Each user creates their own app at https://developer.spotify.com. Controlling playback requires **Spotify Premium**.
We haven't picked a recommended MCP server yet. Contributions are welcome!
