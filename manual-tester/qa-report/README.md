# qa-report

**Command:** `/qa-report [save:<filepath>]`

## Purpose

Compiles a **final QA report** by consolidating all testing activities from the current session — discoveries, test plans, execution results, and verifications — into a professional, stakeholder-ready document.

## What It Does

1. **Gathers findings** from the entire conversation: discovery reports, test plans, execution results, verification results, console errors, network issues, and screenshots.

2. **Classifies findings** by severity:
   - **Critical (P0)** — Data loss, security vulnerability, crash, blocks core flow
   - **Major (P1)** — Feature broken with workaround, wrong data saved
   - **Minor (P2)** — UI glitch, misleading message, cosmetic
   - **Trivial (P3)** — Typo, alignment, polish

3. **Generates a structured report** with executive summary, detailed results, and prioritized recommendations.

## Output

A comprehensive report including:
- **Executive Summary** — Tests executed, pass/fail counts, overall health (RED/YELLOW/GREEN)
- **Critical Findings** — Each bug with reproduction steps, screenshots, suggested fix
- **Test Results Summary** — Pass rates by test suite
- **Console Error Audit** — Errors/warnings per page
- **Network Issue Audit** — Failed API requests
- **Coverage Assessment** — What was tested vs what wasn't
- **Recommendations** — Prioritized as Immediate / Before Release / Backlog

## Usage Examples

```
/qa-report                          # Output report to conversation
/qa-report save:qa-report.md        # Save report to file
```

## Key Principles

- Only reports what was actually tested — never pads with assumed results
- Every bug includes reproduction steps and evidence
- Honest about coverage gaps
- Executive summary readable by non-technical stakeholders
- Recommendations are prioritized and actionable
