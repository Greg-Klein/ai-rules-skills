# AI Rules Skills

Skills and rules repository for the [ai-rules-mcp](https://github.com/Greg-Klein/ai-rules-mcp) MCP server. The server clones this repo and serves skills to Cursor, Claude Code, Cline, Windsurf, etc., so the whole team gets the same AI guidance.

## Usage

1. Point the [ai-rules-mcp](https://github.com/Greg-Klein/ai-rules-mcp) server at this repo via `SKILLS_REPO_URL`.
2. The server syncs this repo on an interval and exposes `get_rules`, `list_skills`, and `get_skill` to your IDE.

## Structure

```
skills/
├── react/SKILL.md
├── typescript/SKILL.md
├── testing/SKILL.md
├── security/SKILL.md
└── java-spring/SKILL.md
```

Each skill lives in `skills/<name>/SKILL.md` with YAML frontmatter:

```yaml
---
name: react
description: React best practices
patterns:
  - "**/*.tsx"
  - "**/*.jsx"
tags: [react, frontend]
priority: high # high | normal | low
always: false # true = always included
---
```

- **patterns**: globs that trigger this skill for a given file path.
- **tags**: for manual activation or filtering.
- **always**: if `true`, the skill is always returned by `get_rules`.

## Adding a skill

1. Create `skills/<skill-name>/SKILL.md` with the frontmatter above and Markdown content.
2. Push to the branch the MCP server follows (default `master`). It will sync on the next interval.
