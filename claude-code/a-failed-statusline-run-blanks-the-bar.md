# A failed status line command blanks the status bar

If the status line command exits non-zero or prints nothing (error exit, timeout, spawn failure, empty output), Claude Code clears the bar text and draws no bar until the next successful run (about 3 s with refreshInterval 3). Only a run cancelled by a newer update keeps the old text.

## Run it yourself

```sh
grep -a -c 'async function nar(' ~/.local/share/claude/versions/2.1.296
```

## What it printed

In the 2.1.296 binary the status line runner returns undefined when the exit status is not 0 or stdout is empty, and the bar is drawn only when it has text.

- Claude Code 2.1.296
- First seen 2026-10-12
- Card: https://optionos.app/discoveries/claude-code/a-failed-statusline-run-blanks-the-bar/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
