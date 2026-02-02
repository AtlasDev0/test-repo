# HEARTBEAT.md — What to Check Every 30 Minutes

## On Wake

1. **Read WORKING.md** — Is there an in-progress task? Resume it.
2. **Check memory/YYYY-MM-DD.md** — Any recent context from today?
3. **Check Mission Control attention cache** — Read `mission-control/.cache/attention.json` (local file only). If there are any items for Atlas, report them (even if the task is `done`).

## Response Rules

- **Nothing to do?** → Reply `HEARTBEAT_OK` (no tool calls)
- **Work found in WORKING.md?** → Resume the task, report back
- **Blocked?** → Report what's blocking you

## Cost Awareness

- Heartbeat interval: **30 minutes**
- NO convex CLI calls in heartbeat (moved to separate cron job)
- Only read local files — O(100) tokens max
- Mission Control checks run via isolated cron job every 15 min
