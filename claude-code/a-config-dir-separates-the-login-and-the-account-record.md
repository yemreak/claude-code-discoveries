# CLAUDE_CONFIG_DIR gives a process its own login and account record

A Claude Code process started with CLAUDE_CONFIG_DIR=<dir> does not read the shared login and writes its account record (.claude.json) into that directory, so another account can be signed in without touching the login or the account record of running sessions.

## Run it yourself

```sh
CLAUDE_CONFIG_DIR=/tmp/hesap-cfg-tanik timeout 40 claude -p 'say ok' --model claude-haiku-4-5
```

## What it printed

"Not logged in · Please run /login". A claude -p run at the same time without the variable answered ok. .claude.json, projects and sessions appeared in the new directory.

- Claude Code 2.1.319
- First seen 2026-11-09
- Card: https://optionos.app/discoveries/claude-code/a-config-dir-separates-the-login-and-the-account-record/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
