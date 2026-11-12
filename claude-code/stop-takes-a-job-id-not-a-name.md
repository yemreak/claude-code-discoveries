# claude stop needs the job id, not the session name

claude stop does not recognise the name given with --name: it exits 1 with "No job matching <name>" and the process stays alive. The same session stops with its job id (the 8 characters printed by claude --bg).

## Run it yourself

```sh
claude --bg --model haiku --name stop-probe 'say ok, use no tools'; claude stop stop-probe; echo "exit $?"; claude stop <job id printed by claude --bg>; echo "exit $?"
```

## What it printed

By name: exit 1 · No job matching 'probe-end-mv7ahlew'. By job id: exit 0 · stopped, and the process ended within 505 ms.

- Claude Code 2.1.296
- First seen 2026-10-14
- Card: https://optionos.app/discoveries/claude-code/stop-takes-a-job-id-not-a-name/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
