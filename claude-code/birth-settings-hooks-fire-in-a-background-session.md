# Hooks passed with --settings run in a background session

A Stop hook given with claude --bg --settings '{"hooks":{"Stop":[…]}}' runs at the end of every turn of that background session. Its input carries session_id, transcript_path, cwd, hook_event_name Stop, stop_hook_active, last_assistant_message, background_tasks and session_crons. The hook applies only to that session and does not touch ~/.claude/settings.json.

## Run it yourself

```sh
claude --bg --model haiku --name stop-probe --settings '{"hooks":{"Stop":[{"hooks":[{"type":"command","command":"cat > /tmp/stop-input.json"}]}]}}' 'say ok, use no tools'; sleep 30; jq -r .hook_event_name /tmp/stop-input.json
```

## What it printed

Stop: the hook ran at the end of the background session's turn and received the Stop input.

- Claude Code 2.1.296
- First seen 2026-10-14
- Card: https://optionos.app/discoveries/claude-code/birth-settings-hooks-fire-in-a-background-session/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
