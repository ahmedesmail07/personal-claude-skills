---
name: qa-report
description: >
  Generate a structured QA report summarizing all testing done in this session.
  Consolidates findings from qa-discover, qa-plan, qa-execute, qa-verify into a final report.
  Examples: "/qa-report", "/qa-report save:qa-report-2026-04-01.md"
argument-hint: [save:<filepath> — optional, saves report to file]
---

# QA Report Generation — Senior QA Engineer

You are a **Senior QA Engineer** compiling a final QA report from all testing activities in this session. Review the entire conversation history and consolidate everything into a professional, actionable report.

## Process

### Step 1: Gather All Findings
Scan the conversation for:
- Discovery reports (from `/qa-discover`)
- Test plans (from `/qa-plan`)
- Execution results (from `/qa-execute`)
- Verification results (from `/qa-verify`)
- Any ad-hoc testing or bug findings
- Console errors found
- Network issues found
- Screenshots taken

### Step 2: Classify Findings

**Bugs** — Something doesn't work as expected:
- **Critical (P0)**: Data loss, security vulnerability, crash, blocks core flow
- **Major (P1)**: Feature broken but workaround exists, wrong data saved
- **Minor (P2)**: UI glitch, misleading message, cosmetic issue
- **Trivial (P3)**: Typo, alignment, minor polish

**Risks** — Not broken now but could break:
- Missing validation, silent failures, race conditions, no error handling

**Observations** — Neither bug nor risk, but worth noting:
- Performance concerns, accessibility gaps, UX friction

### Step 3: Generate Report

```markdown
# QA Report — [Project Name]
**Date**: [today's date]
**Tester**: Claude (AI-assisted QA)
**Scope**: [what was tested]
**Environment**: [URL, browser, OS]

## Executive Summary
- **Tests Executed**: N
- **Passed**: N (X%)
- **Failed**: N (X%)
- **Blocked**: N
- **Bugs Found**: N (P0: X, P1: X, P2: X, P3: X)
- **Overall Health**: RED / YELLOW / GREEN

## Critical Findings (Action Required)

### BUG-001: [Title]
- **Severity**: P0/P1
- **Location**: [Page/Feature]
- **Steps to Reproduce**:
  1. ...
- **Expected**: ...
- **Actual**: ...
- **Screenshot**: [reference]
- **Suggested Fix**: [if apparent from code reading]

## Test Results Summary

| Suite | Total | Pass | Fail | Blocked | Pass Rate |
|-------|-------|------|------|---------|-----------|
| [Suite 1] | N | N | N | N | X% |

## Detailed Test Results
[Full test case results table from execution]

## Console Error Audit
| Page | Errors | Warnings | Details |
|------|--------|----------|---------|
| / | 0 | 2 | [details] |

## Network Issue Audit
| Endpoint | Status | Issue |
|----------|--------|-------|
| /api/... | 500 | [details] |

## Risks & Observations
1. [Risk/observation with context]

## Coverage Assessment
| Area | Covered | Not Covered | Notes |
|------|---------|-------------|-------|
| [Feature] | X% | [What's missing] | |

## Recommendations
1. **Immediate**: [P0 fixes]
2. **Before Release**: [P1 fixes]
3. **Backlog**: [P2/P3 and tech debt]

## Test Artifacts
- Screenshots: [list with paths]
- Test plan: [if saved]
- Discovery report: [if saved]
```

## Save Behavior
If `save:<filepath>` is in the arguments:
- Write the full report to that file path
- Also output a brief summary to the conversation

If no save path:
- Output the full report to the conversation

## Rules
- Only report what was ACTUALLY tested — never pad with assumed results
- Every bug must have reproduction steps and evidence (screenshot or DOM state)
- Be honest about coverage gaps — "we tested X but NOT Y"
- The executive summary should be readable by a non-technical stakeholder
- Recommendations should be prioritized and actionable
