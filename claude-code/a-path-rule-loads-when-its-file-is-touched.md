# A path-scoped rule loads only when a matching file is read

Claude Code puts a project .claude/rules/<name>.md that has paths: frontmatter into context when a matching file is touched: Read, Edit, or a Bash read command that names the file (cat, head, tail, sed -n, rg <pattern> <file>). Searching a directory or the root (rg <pattern> <dir>, rg -l, ls) and wc do not load it, and neither does a Bash command that starts with cd <dir> &&, is piped (|) or redirected. It loads once per session, and a --fork-session fork does not load it again. A file outside the session's project loads no project's rules.

## Run it yourself

```sh
In a project whose .claude/rules/r.md has paths: src/**, start a fresh claude -p --model haiku session for each command form, have it run one read of src/a.ts (cat src/a.ts · rg <pattern> src/a.ts · head src/a.ts · rg <pattern> src · rg <pattern> · rg -l <pattern> src · cd src && head a.ts · head src/a.ts | cut -c1-5) and count nested_memory attachments in each session's transcript.
```

## What it printed

8 of 8 forms matched: cat, rg on the file and head loaded the rule. rg on a directory, rg at the root, rg -l, cd && head and head | cut did not. The attachment carries path, displayPath and content, and no load_reason key.

- Claude Code 2.1.304
- First seen 2026-10-17
- Card: https://optionos.app/discoveries/claude-code/a-path-rule-loads-when-its-file-is-touched/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
