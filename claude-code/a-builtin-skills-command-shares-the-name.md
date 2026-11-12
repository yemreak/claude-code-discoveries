# A skill named skills sits next to the built-in /skills command

Claude Code has a built-in /skills command ("List available skills"). A user skill named skills does not replace it: the / menu shows two /skills rows side by side, and only their descriptions tell them apart.

## Run it yourself

```sh
With a skill at ~/.claude/skills/skills/SKILL.md, type /skills in the Claude Code prompt. Two rows appear; remove that skill directory and only the built-in row "List available skills" remains.
```

## What it printed

Two /skills rows in the / menu: the skill with its own description and the built-in command with "List available skills". No source named skills existed in ~/.claude/commands or in plugin directories.

- Claude Code 2.1.312
- First seen 2026-10-29
- Card: https://optionos.app/discoveries/claude-code/a-builtin-skills-command-shares-the-name/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
