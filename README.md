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

## Auto-sync
Local clone: `~/projects/markettracker`. A Claude Code hook (`~/.claude/hooks/markettracker_sync.py`) keeps it in sync:
- after the routine is read/updated via Claude Code, its prompt and config are written to `routine/prompt.md` and `routine/config.json`
- at the end of every Claude Code turn, any change in the repo is committed, rebased onto origin, and pushed
