# zsh-only expansions trigger the rm prompt even in bypass mode

Claude Code 2.1.309 reads a Bash command with its own bash parser. zsh expansions such as ${(f)…}, ${(j:,:)…}, ${${x}}, ${#${x}}, ${a[(I)…]} and ${a:#…} (also inside double quotes, unquoted heredocs or backticks) leave an ERROR node, and because Claude Code then cannot rule out an rm it asks "Dangerous rm operation not ruled out" even under --dangerously-skip-permissions. In an unattended session the question becomes a refusal after 2 minutes. $x[(I)2], ${~x}, ${=x}, ${+x}, *(N), =(…), single quotes and a quoted heredoc body do not ask.

## Run it yourself

```sh
mkdir -p /tmp/rmprobe2 && cd /tmp/rmprobe2 && printf '%s\n' 'echo ${(j:,:)path}' > c.txt && claude -p --model haiku --dangerously-skip-permissions --settings '{"disableAllHooks":true}' "Run the single line in /tmp/rmprobe2/c.txt exactly with one Bash call (read it with Read first) and quote the tool result verbatim." < /dev/null
```

## What it printed

"Dangerous rm operation not ruled out — the shell may read this command differently than it was parsed" across 4 runs and 33 commands with hooks disabled.

- Claude Code 2.1.309
- First seen 2026-10-23
- Card: https://optionos.app/discoveries/claude-code/an-unparsed-zsh-expansion-asks-under-bypass/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
