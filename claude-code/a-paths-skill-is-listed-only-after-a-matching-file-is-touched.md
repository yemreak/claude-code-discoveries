# A skill with paths: is listed only after a matching file is touched

A skill whose frontmatter has paths (a glob) is not in the skill list at session start. It joins the list when the agent touches a matching file. Its body still does not enter context by itself: opening it is still the model's Skill call.

## Run it yourself

```sh
D=$(mktemp -d) && mkdir -p $D/.claude/skills/yol-deneme $D/notlar && printf -- '---\ndescription: "notlar"\npaths: ["notlar/**"]\n---\nx\n' > $D/.claude/skills/yol-deneme/SKILL.md && echo a > $D/notlar/a.md && cd $D && claude -p 'notlar/a.md dosyasını oku' --model haiku --output-format stream-json --verbose --max-turns 3 --allowedTools Read < /dev/null | grep -c '"name":"yol-deneme"'
```

## What it printed

Listed at session start 0/4. Listed after reading a non-matching file 0/2. Listed after reading a matching file 2/2. Body in context 0/4, Skill calls 0/4.

- Claude Code 2.1.316
- First seen 2026-11-01
- Card: https://optionos.app/discoveries/claude-code/a-paths-skill-is-listed-only-after-a-matching-file-is-touched/

Measured while building [optionOS](https://optionos.app/), which works with Claude Code.
