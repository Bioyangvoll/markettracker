# markettracker
Biweekly product trend memory store for Claude Code agent

## Schedule
- Summary email: **every two weeks, Monday 12:00 Europe/Berlin**
- First biweekly run: **2026-11-02**
- Cloud routine cron: `0 10,11 * * 1` (UTC). The agent proceeds only when
  - the Berlin local hour is 12 (handles CET/CEST switch), and
  - whole weeks since 2026-11-02 is even (biweekly parity).
  Otherwise it exits without searching, committing, or emailing.

## Files
- `memory/findings.md` — findings per run (last 12 runs kept), used to avoid repeats
