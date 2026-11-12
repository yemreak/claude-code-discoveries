# permissions.deny still refuses under bypassPermissions

A permissions.deny rule passed with --settings (Bash(swift build:*), Bash(swiftc:*)) refuses the Bash command even in --permission-mode bypassPermissions and catches a subcommand inside a chained command (cd /tmp && swift build --help). The refusal is fixed text and carries neither the rule's reason nor a way around it. Deny sees only the Bash tool call: a child process started from inside a script does not read this setting.

## Run it yourself

```sh
mkdir -p /tmp/denyprobe && cd /tmp/denyprobe && claude -p --model haiku --permission-mode bypassPermissions --settings '{"permissions":{"deny":["Bash(swift build:*)","Bash(swiftc:*)"]}}' "Run exactly this bash command and report its output or the refusal verbatim: cd /tmp && swift build --help | head -1"
```

## What it printed

Permission to use Bash with command `cd /tmp && swift build --help | head -1` has been denied. The command did not run, in 2 runs.

- Claude Code 2.1.296
- First seen 2026-10-13
- Card: https://optionos.app/discoveries/claude-code/settings-deny-refuses-under-bypass/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
