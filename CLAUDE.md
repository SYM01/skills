# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Personal agent-skill hub for SYM01, distributed publicly at `github.com/SYM01/skills` and installed on any machine via:

```bash
npx skills add SYM01/skills
```

It uses the [vercel-labs/skills](https://github.com/vercel-labs/skills) ecosystem. There is no build step, no package.json, no test suite — the deliverables are markdown files (`SKILL.md`) that get loaded into agent context at runtime.

## Repo layout

```
skills/<name>/SKILL.md   ← every skill is a single file at this path
README.md                ← install instructions + table of skills
```

`npx skills` auto-discovers any directory under `skills/` containing a `SKILL.md`. No manifest, no plugin.json, no marketplace.json. Don't add scaffolding the CLI doesn't need.

## SKILL.md authoring contract

Each skill is one file with YAML frontmatter and a markdown body:

```markdown
---
name: <skill-name>            # must match the directory name
description: <one paragraph>  # see below — this is the trigger surface
---

# Body
...
```

**The `description` field is the trigger surface.** Agents (Claude Code, etc.) decide whether to load a skill by matching this text against the user's intent. Write it to maximize recall on the verbs and nouns a user would naturally say — not just "X skill". `skills/plan-doctor/SKILL.md` is the canonical example: it lists every phrasing that should activate it ("make a plan", "outline an approach", "break this down", entering plan mode). Mirror that density when adding new skills.

The body is plain markdown. No required sections, but `plan-doctor` follows a useful shape: *When this skill applies* → *What to do* → *What not to do*. Reuse that structure unless there's a reason not to.

## Adding a new skill

1. `mkdir -p skills/<name>`
2. Write `skills/<name>/SKILL.md` with the frontmatter above.
3. Append a row to the Skills table in `README.md`.
4. Verify locally (next section).
5. Commit and push.

## Verifying locally before pushing

The cheapest end-to-end check that the CLI parses the repo correctly:

```bash
npx --yes skills@latest add ./ --list
```

Expected: every skill under `skills/` is listed with its `description`. If a skill is missing, the frontmatter is malformed or the directory is in the wrong place — fix before pushing.

## GitHub repo metadata

The `github.com/SYM01/skills` repo has its description, homepage (`https://skills.sh/SYM01/skills`), and topics already set via `gh repo edit`. If you change the README's headline phrasing or add categories of skills, update the repo description and topics to match — they're visible on the GitHub project page and on `skills.sh`.
