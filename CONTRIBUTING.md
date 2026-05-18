# Contributing

## Scope

This project focuses on Chinese blog and technical article review. Keep the skill practical, concise, and review-oriented.

Good additions:

- Sharper review criteria.
- Better output templates.
- Chinese technical writing edge cases.
- Copy-formatting rules that are hard to remember but useful during review.

Avoid:

- Turning the skill into a generic writing assistant.
- Adding scripts before there is a repeatable automation need.
- Adding project-specific brand voice rules.
- Duplicating long upstream style guides.

## Skill Quality Bar

Before proposing changes:

1. Keep `SKILL.md` short and trigger-focused.
2. Put detailed review guidance under `references/`.
3. Do not force the agent to rewrite articles by default.
4. Preserve the author's voice unless clarity or correctness is affected.
5. Dogfood: run this skill against its own changed `.md` files. If the skill flags issues in its own copy, fix them before merging. This catches regressions in clarity, structure, and Chinese copy formatting.

Structural validation is left to the installer (`npx skills add` reports frontmatter or schema errors at install time) and to the runtime (Claude Code and other agents fail loudly if `SKILL.md` is malformed). No custom validation script is needed.
