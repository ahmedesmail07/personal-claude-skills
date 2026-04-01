# personal-claude-skills

A curated collection of custom Claude Code skills for automating real-world development workflows.

## Skills

### [Manual Tester](./manual-tester/)

A complete QA testing suite that turns Claude into a Senior QA Engineer. Five skills that cover the full testing lifecycle:

| Skill | Purpose |
|-------|---------|
| `qa-discover` | Extract business logic and testable behaviors from code |
| `qa-plan` | Generate structured test cases with exact steps and data |
| `qa-execute` | Run tests in a real browser via Playwright MCP |
| `qa-verify` | Deep verification of a specific bug or behavior |
| `qa-report` | Compile findings into a stakeholder-ready report |

## Usage

These skills can be installed as:

- **Global skills** — Place under `~/.claude/skills/` to use across all projects
- **Project skills** — Place under `.claude/skills/` within a specific repo

Invoke any skill with its slash command (e.g., `/qa-discover`, `/qa-execute http://localhost:3000`).

## Requirements

- [Claude Code](https://claude.ai/code) CLI or IDE extension
- [Playwright MCP server](https://github.com/anthropics/anthropic-mcp-playwright) (for `qa-execute` and `qa-verify`)
