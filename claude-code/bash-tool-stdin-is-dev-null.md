# The Bash tool's stdin is /dev/null in a background session

In a background (claude --bg) session the Bash tool's stdin is the /dev/null character device, both in the foreground and with run_in_background, so reading stdin returns empty at once instead of waiting.

## Run it yourself

```sh
In a claude --bg session, have the Bash tool run stat -L -f %HT /dev/stdin and bun -e 'await Bun.stdin.text()' with a 5 s guard.
```

## What it printed

Character Device. Bun.stdin.text() returned without hitting the 5 s guard.

- Claude Code 2.1.296
- First seen 2026-10-10
- Card: https://optionos.app/discoveries/claude-code/bash-tool-stdin-is-dev-null/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
