# Integrations

Monday uses [MCP servers](https://modelcontextprotocol.io) to talk to each service. Authentication happens through OAuth when you run `/mcp` in Claude Code.

## Jira (bundled)

Atlassian's official remote MCP server: `https://mcp.atlassian.com/v2/mcp`.
Run `/mcp`, pick **atlassian** and sign in. Your Atlassian admin may need to allow the integration.
Docs: https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/

## Notion (bundled)

Notion's official remote MCP server: `https://mcp.notion.com/mcp`.
Run `/mcp`, pick **notion** and sign in. Choose which pages and workspaces Monday can see.
Docs: https://developers.notion.com/guides/mcp/get-started-with-mcp

## Slack (official plugin)

Slack publishes its own Claude Code plugin with the official MCP server (`https://mcp.slack.com/mcp`):

```
/plugin install slack
```

Your **Slack workspace admin must approve MCP integration** before you can authenticate.
Docs: https://docs.slack.dev/ai/slack-mcp-server/connect-to-claude

## Outlook Calendar (optional, TODO)

Uses Microsoft Graph. Requires an app registration in Microsoft Entra ID (Azure), and many company tenants block user consent, so check with IT.
We haven't picked a recommended MCP server yet. Contributions are welcome!

## Spotify (optional, TODO)

Uses the Spotify Web API. Each user creates their own app at https://developer.spotify.com. Controlling playback requires **Spotify Premium**.
We haven't picked a recommended MCP server yet. Contributions are welcome!
