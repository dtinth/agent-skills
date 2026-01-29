---
name: agent-skills
description: Manage project-specific skills in the .claude/skills directory. Use this skill to understand skill structure, create new skills, or improve existing skills based on work session learnings.
---

# Agent Skills

- Agent skills in this project are stored in `.claude/skills/` directory
- Each skill is a folder with a `SKILL.md` file inside it
- The skill folder name must match the `name` field in the SKILL.md frontmatter
- The frontmatter requires `name` (lowercase alphanumeric with hyphens only, no start/end hyphens, no consecutive hyphens) and `description` (describes what the skill does and when to use it)
- The Markdown body after the frontmatter contains the skill instructions with no format restrictions
- Skills can have optional subdirectories: `scripts/` for executable code, `references/` for documentation, `assets/` for templates and resources
- Keep the main SKILL.md body under 500 lines for efficiency; move detailed reference material to separate files in `references/`
- When referencing other files in a skill, use relative paths from the skill root (e.g., `references/REFERENCE.md` or `scripts/extract.py`)
- File references should be one level deep from SKILL.md to avoid deeply nested reference chains
- All skill improvements should be made by editing the SKILL.md file in place, since skills are Git-tracked files in the codebase
- When improving a skill based on work session learnings, edit the SKILL.md file to reflect new insights
- After updating a skill file, the next agent session will load the improved skill automatically
- Progressive disclosure keeps skills efficient: metadata loads at startup (~100 tokens), full instructions load on activation (<5000 tokens recommended), resources load on demand
- Test your skill improvements by thinking through: Does the description clearly indicate when to use it? Are the instructions clear and self-contained? Can the agent follow them without additional context?
- Document why you're making a skill improvement in the Git commit message if the change needs explanation
