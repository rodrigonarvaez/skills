# Agent Skills

A personal collection of custom skills for [Claude Code](https://claude.ai/code) and other AI Agents. Each skill extends the AI Agent with structured methodology, domain knowledge, or guided workflows.

## Skills

| Skill                                   | Description                                                                                 |
| --------------------------------------- | ------------------------------------------------------------------------------------------- |
| [sprint-method](sprint-method/SKILL.md) | Guide through the full Design Sprint methodology — from problem mapping to tested prototype |
| [startup-scaffolding](startup-scaffolding/SKILL.md) | Generate a complete investor-grade documentation suite for a new startup or product idea — Vision, Validation, PRD, AI Instructions, Project Description, and repo stubs |

## Installation

Skills are managed with the [skills CLI](https://github.com/vercel-labs/skills) — a tool for installing and managing reusable instruction sets across 40+ coding agents.

Install this collection into your project:

```bash
npx skills add rodrigonarvaez/skills
```

Or globally, to make skills available across all projects:

```bash
npx skills add -g rodrigonarvaez/skills
```

To install a specific skill only:

```bash
npx skills add rodrigonarvaez/skills --skill sprint-method
```

Once installed, invoke a skill by naming it or just describe your intent — the agent will trigger the skill automatically based on the trigger phrases defined in each `SKILL.md`.

## Structure

Each skill lives in its own directory:

```
<skill-name>/
├── SKILL.md          # Skill definition, instructions, and trigger phrases
└── references/       # Supporting context files loaded per phase or topic
```

## Adding a Skill

1. Create a new directory: `<skill-name>/`
2. Add a `SKILL.md` with a frontmatter block containing `name`, `version`, and `description`
3. Add any reference files in a `references/` subdirectory


## Tested Agents

| Agent                                 | Notes                                                 |
| ------------------------------------- | ----------------------------------------------------- |
| [Claude Code](https://claude.ai/code) | Primary target — all skills developed and tested here |
