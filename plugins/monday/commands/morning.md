---
description: Morning briefing — today's meetings, tickets, mentions and notes
---

Use the `monday` skill persona. Build the user's morning briefing for today.

Gather, using whatever connectors are available (skip missing ones silently, then list them at the end in one line):

1. **Calendar** (Outlook) — today's meetings with times, and the first free block of 1h+ for focus.
2. **Jira** — tickets assigned to the user that are In Progress, In Review, or Blocked; anything due today or overdue.
3. **Slack** — unread DMs and mentions since yesterday evening; flag anything that looks urgent.
   **Email** (Outlook) — unread emails since yesterday evening that are flagged, marked important or come from people the user works with; skip newsletters and notifications.
4. **GitHub / GitLab** — PRs/MRs waiting for the user's review; the user's own open PRs/MRs with failing CI, requested changes or new comments.
5. **Notion** — pages the user edited or was mentioned in during the last day, and any to-do list for today.

Format:

- One-line greeting with a light, friendly touch.
- **Atenção primeiro**: the 1–3 things that need action soonest.
- Then short sections: Agenda · Tickets · Code review · Mensagens (Slack + e-mail) · Notas.
- End with one suggestion for how to start the day (e.g. "bloqueio 10h–12h pra focar no PROJ-123?"). Do not act on it without confirmation.

$ARGUMENTS
