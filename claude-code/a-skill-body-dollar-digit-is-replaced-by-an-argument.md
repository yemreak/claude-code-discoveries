# $0, $1 … in a skill body are replaced by arguments, even inside !`…` commands

Claude Code replaces $<digit> ($0, $1 …) in a skill body with the call's arguments, including inside !`…` command lines, so the shell's or awk's own $0 is overwritten. Called without arguments nothing shows; called with an argument the command breaks. Write $(0) or a variable instead.

## Run it yourself

```sh
In a scratch project create a skill whose body is !`echo A$0B` and call it as /<skill> x. Output AxB means the replacement happens. !`echo A$(0)B` is not replaced.
```

## What it printed

Called with the first argument -, an awk line in a skill body ran as print n " · " - and awk reported a syntax error. With $(0) the same line ran without error.

- Claude Code 2.1.312
- First seen 2026-10-29
- Card: https://optionos.app/discoveries/claude-code/a-skill-body-dollar-digit-is-replaced-by-an-argument/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
