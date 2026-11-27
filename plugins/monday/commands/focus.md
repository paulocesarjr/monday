---
description: Focus mode — find focus time, set Slack status, play focus music
argument-hint: "[duration, e.g. 90m] [task or ticket]"
---

Use the `monday` skill persona. The user wants to enter focus mode.

Arguments: $ARGUMENTS (duration defaults to 90 minutes if not given).

Propose a plan, then wait for confirmation before doing anything:

1. **Calendar** (Outlook) — check for conflicts in the window; offer to block it as "Focus".
2. **Slack** — offer to set status to 🎧 "Focus — back at HH:MM" and pause notifications.
3. **Spotify** — offer to play a focus playlist (lo-fi, instrumental, or the user's favorite).
4. **Task** — if a ticket or task was mentioned, show its summary and acceptance criteria.

Show the plan as a short checklist and ask "Posso?". Skip steps whose connector isn't installed.
