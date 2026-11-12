# Claude Code discoveries

First-hand observations of how Claude Code behaves: each one states a claim, the command that shows it, what the command printed, and the Claude Code version it was seen on. Run the command yourself to check it on your version.

| Observation | Claude Code | First seen |
|---|---|---|
| [CLAUDE_CONFIG_DIR gives a process its own login and account record](claude-code/a-config-dir-separates-the-login-and-the-account-record.md) | 2.1.319 | 2026-11-09 |
| [The paste hint hides prompt-hint plugin output for 8 seconds](claude-code/a-paste-hint-keeps-mods-off-the-prompt-hint.md) | 2.1.319 | 2026-11-07 |
| [A skill with paths: is listed only after a matching file is touched](claude-code/a-paths-skill-is-listed-only-after-a-matching-file-is-touched.md) | 2.1.316 | 2026-11-01 |
| [Rejecting a Bash call does not undo what it already started](claude-code/a-rejected-loop-call-may-have-already-spawned.md) | 2.1.312 | 2026-10-29 |
| [A skill named skills sits next to the built-in /skills command](claude-code/a-builtin-skills-command-shares-the-name.md) | 2.1.312 | 2026-10-29 |
| [$0, $1 … in a skill body are replaced by arguments, even inside !`…` commands](claude-code/a-skill-body-dollar-digit-is-replaced-by-an-argument.md) | 2.1.312 | 2026-10-29 |
| [zsh-only expansions trigger the rm prompt even in bypass mode](claude-code/an-unparsed-zsh-expansion-asks-under-bypass.md) | 2.1.309 | 2026-10-23 |
| [A live session record does not say who opened the session](claude-code/a-live-session-record-names-no-opener.md) | 2.1.302 | 2026-10-18 |
| [A path-scoped rule loads only when a matching file is read](claude-code/a-path-rule-loads-when-its-file-is-touched.md) | 2.1.304 | 2026-10-17 |
| [claude stop needs the job id, not the session name](claude-code/stop-takes-a-job-id-not-a-name.md) | 2.1.296 | 2026-10-14 |
| [claude --bg refuses --print](claude-code/background-and-print-conflict.md) | 2.1.296 | 2026-10-14 |
| [Hooks passed with --settings run in a background session](claude-code/birth-settings-hooks-fire-in-a-background-session.md) | 2.1.296 | 2026-10-14 |
| [permissions.deny still refuses under bypassPermissions](claude-code/settings-deny-refuses-under-bypass.md) | 2.1.296 | 2026-10-13 |
| [A failed status line command blanks the status bar](claude-code/a-failed-statusline-run-blanks-the-bar.md) | 2.1.296 | 2026-10-12 |
| [A Bash timeout moves the command to the background without a signal](claude-code/bash-timeout-backgrounds-without-signal.md) | 2.1.296 | 2026-10-12 |
| [Selecting text in Claude Code inside Ghostty copies it to the general pasteboard](claude-code/terminal-selection-is-a-general-pasteboard-copy.md) | 2.1.296 | 2026-10-11 |
| [The Bash tool's stdin is /dev/null in a background session](claude-code/bash-tool-stdin-is-dev-null.md) | 2.1.296 | 2026-10-10 |

17 observations. The same cards live at https://optionos.app/discoveries/.

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
