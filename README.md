# destiller

Agent skill that compresses a draft to the fewest words while keeping every material claim. Manual-only: it never auto-triggers. Follows the open [Agent Skills](https://agentskills.io) format, so it works in Claude Code, Codex, and any other host that reads `SKILL.md`.

## Install

Clone into your host's skills directory:

```bash
# Claude Code
git clone https://github.com/jedruch/destiller ~/.claude/skills/destiller

# Codex
git clone https://github.com/jedruch/destiller ~/.codex/skills/destiller
```

Restart the agent, then invoke it explicitly:

```
/destiller [--tight|--keep-tone] <draft text or file path>   # Claude Code
$destiller <draft text or file path>                         # Codex
```

With no argument it compresses the assistant's last message.

## Layout

- `SKILL.md`: the skill. Frontmatter keys `argument-hint` and `disable-model-invocation` are Claude Code extensions; other hosts ignore them.
- `agents/openai.yaml`: Codex display metadata and invocation policy.
