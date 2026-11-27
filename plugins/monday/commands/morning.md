---
description: Morning briefing — today's meetings, tickets, mentions and notes
---

Use the `monday` skill persona. Build the user's morning briefing for today.

Gather, using whatever connectors are available (skip missing ones silently, then list them at the end in one line):

1. **Calendar** — today's meetings with times, and the first free block of 1h+ for focus.
2. **Jira** — tickets assigned to the user that are In Progress, In Review, or Blocked; anything due today or overdue.
3. **Slack** — unread DMs and mentions since yesterday evening; flag anything that looks urgent.
4. **Notion** — pages the user edited or was mentioned in during the last day, and any to-do list for today.

Format:

- One-line greeting with a light, friendly touch.
- **Atenção primeiro**: the 1–3 things that need action soonest.
- Then short sections: Agenda · Tickets · Mensagens · Notas.
- End with one suggestion for how to start the day (e.g. "bloqueio 10h–12h pra focar no PROJ-123?"). Do not act on it without confirmation.

$ARGUMENTS
