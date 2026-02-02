# Agent Skills (JS/TS)

[Agent Skills](https://agentskills.io/home) are a vendor-neutral format for giving agents instructions and expertise. This repo contains skills for JavaScript/TypeScript, aligned with the [Agent Skills specification](https://agentskills.io/specification). They work with any product or tool that supports the format—no dependency on a specific vendor.

## Skills

| Skill | Description |
|-------|-------------|
| **js-ts-performance-readability** | Performant, readable JS/TS for scripts, utilities, data processing, and performance-sensitive code. Model problems first, handle edge cases, explicit types, Map/Set for lookups, async patterns, small helpers. |
| **js-ts-business-crud-transforms** | JS/TS for business apps (frontend + backend): CRUD, API integration, data transforms. Model-first, validate at boundaries, single-pass over lists, typed API vs UI. |

Each skill lives in `skills/<skill-name>/` with a required `SKILL.md` (YAML frontmatter + Markdown body). The directory name must match the `name` field in frontmatter per the spec.

## Using these skills

### Skills CLI

Install skills directly using the [skills CLI](https://skills.sh/docs/cli):

```bash
npx skills add icyJoseph/agent-skills
```

### Claude Code (manual)

Copy a skill directory to your personal or project skills folder:

```bash
# Personal (available in all projects)
cp -r skills/js-ts-performance-readability ~/.claude/skills/

# Project-specific
cp -r skills/js-ts-performance-readability .claude/skills/
```

Once installed, Claude Code will automatically use the skill when relevant, or you can invoke it directly with `/js-ts-performance-readability`.

See [Claude Code skills documentation](https://docs.claude.com/en/docs/claude-code/skills) for more details.

### Other tools

Copy the **skill directory** (e.g. `skills/js-ts-performance-readability`) into your environment's skills location. Where that is depends on your agent or tool—see its documentation.

Products that support the [Agent Skills format](https://agentskills.io/specification) load skills by `name` and `description` from `SKILL.md`; no vendor-specific wiring in the skill files themselves.

## Format (spec-aligned)

- **[Specification](https://agentskills.io/specification)**: Required frontmatter `name` (matches dir name, ≤64 chars, lowercase + hyphens) and `description` (≤1024 chars). Optional: `license`, `compatibility`, `metadata`, `allowed-tools`. Body: Markdown instructions.
- **Progressive disclosure**: Keep `SKILL.md` under ~500 lines; put long reference material in `references/` or `scripts/` and link from the body.
- **Validation**: Use [skills-ref](https://github.com/agentskills/agentskills/tree/main/skills-ref) to validate: `skills-ref validate ./skills/js-ts-performance-readability` (or your path).

## License

Use and adapt as you like. No warranty.
