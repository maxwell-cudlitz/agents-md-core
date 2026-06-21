---
name: repo-maintenance
description: Instructions for maintaining this repo and registering new MD files. Use when creating or modifying MD files in agents-md-core.
---

# Repo Maintenance

When adding a new `.md` file to this repository:

1. **Add YAML frontmatter** to the new file:
   ```yaml
   ---
   name: short-kebab-name
   description: One sentence describing when this file should be loaded.
   ---
   ```

2. **Register it as a skill** in `~/.kiro/agents/developer.json` by adding a `skill://` entry to the `resources` array:
   ```json
   "skill:///Users/maxwellcudlitz/repos/agents-md-core/NEW_FILE.md"
   ```

3. If the file should be **always loaded** (not on-demand), use `file://` instead of `skill://`.

## Naming Conventions

- Filenames: `UPPER_SNAKE_CASE.md`
- Frontmatter `name`: lowercase kebab-case
- Frontmatter `description`: starts with what it covers, ends with when to use it

## Current Registry

| File | Type | When Loaded |
|------|------|-------------|
| `AGENTS.md` | `file://` | Always |
| `PYTHON.md` | `skill://` | Python work |
| `DESIGN_FEATURE.md` | `skill://` | Feature design |
| `REPO_MAINTENANCE.md` | `skill://` | Adding/modifying files in this repo |
