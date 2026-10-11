# destiller

Claude Code skill that compresses a draft to the fewest words while keeping every material claim. Manual-only: it never auto-triggers.

## Install

Copy `SKILL.md` into a `destiller/` folder in your skills directory:

```bash
git clone https://github.com/jedruch/destiller ~/.claude/skills/destiller
```

Restart Claude Code, then run:

```
/destiller [--tight|--keep-tone] <draft text or file path>
```

With no argument it compresses the assistant's last message.
