# Rejecting a Bash call does not undo what it already started

Background processes that a Bash call started before it was rejected are not killed by the rejection: what the loop started keeps running and finishes its work. An agent that reads "The tool use was rejected" as "nothing happened" starts the same work twice. After a rejection, count what was started.

## Run it yourself

```sh
Run a long loop command whose every step starts a background process, keep it waiting at the permission prompt and reject it, then count the processes it started (ps). More than 0 means the rejection did not undo the part of the call that had already started.
```

## What it printed

A single Bash call that started 8 agents one after another was rejected and returned "The tool use was rejected". The first 3 agents ran anyway and returned their results 12 to 22 minutes later.

- Claude Code 2.1.312
- First seen 2026-10-29
- Card: https://optionos.app/discoveries/claude-code/a-rejected-loop-call-may-have-already-spawned/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
