# SYM01/skills

Personal skill hub for daily tasks across Claude Code, Codex, Cursor, and any other agent that supports the [open agent skills](https://github.com/vercel-labs/skills) spec.

## Install

Install all skills from this hub:

```bash
npx skills add SYM01/skills
```

Other useful variants:

```bash
# List available skills without installing
npx skills add SYM01/skills --list

# Install a single skill
npx skills add SYM01/skills --skill plan-doctor

# Install into a specific agent (e.g. Claude Code)
npx skills add SYM01/skills -a claude-code

# Non-interactive (CI / scripting)
npx skills add SYM01/skills --skill plan-doctor -a claude-code -y
```

## Skills

| Skill | Description |
| --- | --- |
| [plan-doctor](skills/plan-doctor/SKILL.md) | Reviews and reinforces engineering plans against a standard checklist (dependency currency, agent team mode, formatter/linter completion gate, OpenAPI for multi-module APIs, design tokens for UI work, markdown task lists for complex plans). |

## Adding a new skill

Drop a directory under `skills/<name>/` containing a `SKILL.md` with YAML frontmatter (`name`, `description`). That's the whole contract — `npx skills` auto-discovers it.
