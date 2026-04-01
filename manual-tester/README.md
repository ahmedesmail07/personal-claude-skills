# Manual Tester — QA Skills Suite

A collection of Claude Code skills that turn Claude into a **Senior QA Engineer**. These five skills form a complete manual testing workflow — from discovering what to test, through planning and execution, to final reporting.

## Skills Overview

| Skill | Command | Purpose |
|-------|---------|---------|
| [qa-discover](./qa-discover/) | `/qa-discover` | Reverse-engineer testable specs from code |
| [qa-plan](./qa-plan/) | `/qa-plan` | Generate structured test cases with exact steps and data |
| [qa-execute](./qa-execute/) | `/qa-execute` | Run tests against a live app via Playwright browser automation |
| [qa-verify](./qa-verify/) | `/qa-verify` | Deep-dive verification of a single behavior or bug |
| [qa-report](./qa-report/) | `/qa-report` | Consolidate all findings into a stakeholder-ready report |

## Recommended Workflow

```
1. /qa-discover [path]        -- Understand what the app does
2. /qa-plan from:report.md    -- Turn discoveries into test cases
3. /qa-execute http://...     -- Execute tests in a real browser
4. /qa-verify [specific bug]  -- Drill into anything suspicious
5. /qa-report save:report.md  -- Compile the final QA report
```

## Requirements

- **Playwright MCP server** must be configured for `qa-execute` and `qa-verify` (they drive a real browser).
- The other skills (`qa-discover`, `qa-plan`, `qa-report`) work purely through code analysis and conversation — no browser needed.

## Installation

These skills are installed as Claude Code project skills. Place them under `.claude/skills/` in any project, or keep them as global skills under `~/.claude/skills/`.

## Framework Support

Works with any web framework/language — Django, React, Next.js, Express, Vue, Angular, Rails, etc. The discovery phase auto-detects the framework and adapts accordingly.
