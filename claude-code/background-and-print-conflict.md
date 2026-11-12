# claude --bg refuses --print

Given --bg and --print together, Claude Code exits with code 1 without starting a session. A background session cannot take headless mode's answer-and-exit behaviour and does not close by itself when its turn ends.

## Run it yourself

```sh
claude --bg -p x; echo "exit $?"
```

## What it printed

exit 1 · --bg and --print conflict: --print never starts the interactive session that `claude agents` attaches to, so the job would be unattachable

- Claude Code 2.1.296
- First seen 2026-10-14
- Card: https://optionos.app/discoveries/claude-code/background-and-print-conflict/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
