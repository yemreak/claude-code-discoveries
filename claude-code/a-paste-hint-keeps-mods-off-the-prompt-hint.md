# The paste hint hides prompt-hint plugin output for 8 seconds

After a collapsed paste (over 800 characters or more than 2 line breaks) Claude Code shows "paste again to expand" for 8000 ms and treats the hint line as interactive: during that time the PromptHint render hook is not called, so everything a plugin draws there disappears. Enter does not end the 8 s. Pasting the same text again expands it and closes the hint at once.

## Run it yourself

```sh
grep -a -c 'useHasRenderHooks("PromptHint")&&!H' ~/.local/share/claude/versions/2.1.319
```

## What it printed

1. In an isolated terminal with a real PromptHint plugin, paste then Enter left the hint row empty for 8008 ms. The sent text appeared once in the transcript, byte for byte.

- Claude Code 2.1.319
- First seen 2026-11-07
- Card: https://optionos.app/discoveries/claude-code/a-paste-hint-keeps-mods-off-the-prompt-hint/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
