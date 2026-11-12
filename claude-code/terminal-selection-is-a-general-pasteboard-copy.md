# Selecting text in Claude Code inside Ghostty copies it to the general pasteboard

In Claude Code running in Ghostty, text selected with the mouse is not a Ghostty selection: Claude Code tracks the mouse itself and writes the selection to the general pasteboard as plain text. The focused Ghostty surface's AXSelectedText stays empty (kAXErrorNoValue -25212) and Ghostty's named selection pasteboard (com.mitchellh.ghostty.selection) does not change.

## Run it yourself

```sh
osascript -l JavaScript -e 'ObjC.import("AppKit"); $.NSPasteboard.generalPasteboard.changeCount' before and after drag-selecting text in Claude Code running in Ghostty 1.3.1
```

## What it printed

General pasteboard change count 1070 → 1072. Ghostty's named selection pasteboard stayed at 11. The focused surface's AXSelectedText returned -25212.

- Claude Code 2.1.296
- First seen 2026-10-11
- Card: https://optionos.app/discoveries/claude-code/terminal-selection-is-a-general-pasteboard-copy/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
