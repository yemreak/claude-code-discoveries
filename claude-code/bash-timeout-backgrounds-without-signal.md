# A Bash timeout moves the command to the background without a signal

When a foreground Bash call times out, Claude Code sends the child process no signal (no TERM, INT or HUP). It returns the call with "moved to the background (ID: <id>)" and the process stays as it is (still stopped if it stopped itself with SIGSTOP). The agent is blocked until the timeout and reads messages that arrived meanwhile only after the tool returns. A stopped process dies at once only on SIGKILL; SIGTERM waits for SIGCONT. Killed with SIGKILL, the background task reports exit code 137.

## Run it yourself

```sh
Have Claude Code run, in the foreground with Bash timeout 8000, a script that traps TERM, INT and HUP into a log file and then stops itself with kill -STOP $$. After the tool returns, run ps -o stat= -p <pid> and read the log.
```

## What it printed

After 8 s the tool returned "moved to the background". The log stayed empty. The process was still TN (stopped) 14.7 s later. kill -KILL removed it and the task reported "failed with exit code 137".

- Claude Code 2.1.296
- First seen 2026-10-12
- Card: https://optionos.app/discoveries/claude-code/bash-timeout-backgrounds-without-signal/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
