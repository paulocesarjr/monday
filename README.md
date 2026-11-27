# M.O.N.D.A.Y. 🗓️

```
        o       o
    .---|-------|---.
    |  M O N D A Y  |
    |---------------|
    |   ^       ^   |
    |               |
    |    \_____/    |
    '---------------'
```

> **M**eetings, **O**bjectives, **N**otes, **D**eadlines, **A**lerts & **Y**ou
>
> A friendly daily assistant for developers. Inspired by the AI sidekicks we grew up watching in movies.

Monday is a [Claude Code](https://code.claude.com) plugin that brings your calendar, notes, tickets, chat and music into a single conversation, with a warm personality and a "read freely, write carefully" safety rule.

```
> /monday:morning

Bom dia, Paulo! ☀️ Café pronto? Here's your day:

Atenção primeiro
• Sprint review at 10:00, and PROJ-482 is still "In Review"
• Ana asked about the deploy in #squad-payments (2h ago)
...
```

## Features

| Command | What it does |
|---|---|
| `/monday:setup` | Friendly onboarding: gets to know you and connects your tools |
| `/monday:morning` | Morning briefing: meetings, tickets, PRs/MRs to review, mentions, notes |
| `/monday:daily` | Drafts your standup (yesterday / today / blockers) |
| `/monday:focus 90m PROJ-123` | Blocks time, sets Slack status, plays focus music |

You can also just talk to it: *"Monday, what's on my plate this afternoon?"*

## Install

Inside Claude Code:

```
/plugin marketplace add paulocesarjr/monday
/plugin install monday@monday
```

Then run **`/monday:setup`**. Monday will introduce herself, ask a few questions (name, role, working hours...) and walk you through connecting each service via OAuth (no API keys to paste).

Your profile is saved locally at `~/.monday/profile.md`. It never leaves your machine or goes into any repo, and you can edit it anytime.

### Integrations

| Service | Status | How |
|---|---|---|
| GitHub | ✅ Chosen in setup | Official GitHub MCP (token via `gh` or PAT) |
| GitLab | ✅ Chosen in setup | Built-in GitLab MCP, gitlab.com or self-hosted (OAuth) |
| Jira | ✅ Bundled | Atlassian remote MCP |
| Notion | ✅ Bundled | Notion remote MCP |
| Slack | ✅ Bundled | Official Slack remote MCP (your workspace admin must approve MCP) |
| Outlook (mail + calendar) | ✅ Chosen in setup | Community Microsoft 365 MCP, work or personal account (device code sign-in) |
| Spotify | 🧪 Optional | See [docs/integrations.md](docs/integrations.md) (Premium required for playback) |

Monday works with whatever subset you install. Missing connectors are skipped.

## Safety

Monday reads freely, but **asks before doing anything others can see or that changes state**: sending messages, moving tickets, creating meetings, editing pages. Claude Code's own permission prompts apply on top of that.

## Contributing

PRs welcome. New commands, new integrations (Google Calendar, Linear, Bitbucket...) and translations are all great first contributions. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Disclaimer

Monday is an independent open-source project. It is not affiliated with Marvel, Disney, monday.com, Anthropic, Atlassian, Notion, Slack, Microsoft or Spotify.

## License

[MIT](LICENSE)
