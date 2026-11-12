# A live session record does not say who opened the session

Claude Code's live session record (~/.claude/sessions/<pid>.json) has no parent, opener or origin field. Which session or agent started a session cannot be read from it, only from records the opener keeps itself.

## Run it yourself

```sh
for f in ~/.claude/sessions/*.json; do jq -r "keys|join(\",\")" "$f"; done | sort | uniq -c
```

## What it printed

Three key sets across 63 records (cwd, entrypoint, jobId, kind, messagingSocketPath, name, pid, sessionId, startedAt, status, version and similar). None of them is parent, opener or origin.

- Claude Code 2.1.302
- First seen 2026-10-18
- Card: https://optionos.app/discoveries/claude-code/a-live-session-record-names-no-opener/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
