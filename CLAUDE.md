# CLAUDE.md

## Git Commit Rules

- Commit messages must NOT contain any reference to "Claude", "Claude Code",
  "Anthropic", or "Co-Authored-By: Claude". Keep all commit messages clean
  of AI tool branding — they should read as if written by a human developer.
- Use conventional commits format: `feat:`, `fix:`, `docs:`, `refactor:`,
  `chore:`, `test:`.

## Project Context

This is `ei-skill`, a personal collection of Claude Code skills for
engineering productivity. Each skill lives in its own subdirectory with
`SKILL.md` as the entry point.

## Skill Development

- Follow the skill-creator conventions: YAML frontmatter with `name` and
  `description`, body in imperative form, progressive disclosure via
  `references/` directory.
- Keep SKILL.md lean (under 3000 words); move detailed docs to references/.
