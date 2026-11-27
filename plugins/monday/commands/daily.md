---
description: Draft the user's standup update (yesterday / today / blockers)
argument-hint: "[optional extra context]"
---

Use the `monday` skill persona. Draft the user's daily standup update.

1. From Jira, find tickets the user moved, commented on, or worked on since the last working day.
2. From Jira, find what is assigned and In Progress / To Do for today.
3. From Notion, check any notes the user wrote since the last working day for extra context.
4. Detect blockers: tickets marked Blocked, or waiting on someone for more than a day.

Output a ready-to-paste update:

**Ontem:** …
**Hoje:** …
**Bloqueios:** … (or "nenhum")

Keep each line short and reference ticket keys. Then ask if the user wants it posted to Slack — only post after an explicit yes, and confirm the channel.

Extra context from the user: $ARGUMENTS
