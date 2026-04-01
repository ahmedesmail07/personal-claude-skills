# qa-verify

**Command:** `/qa-verify <behavior-or-bug-description> [url:<base-url>]`

## Purpose

Performs **deep, focused verification** of a single behavior, reported bug, or applied fix. Unlike broad test execution (`qa-execute`), this skill drills into **one thing** and verifies it thoroughly from every angle — DOM state, console, network, JavaScript state, and visual.

## What It Does

1. **Understand** — Reads the bug report, code diff, or behavior description
2. **Set up observation** — Navigates to the page, captures baseline (snapshot, console, screenshot)
3. **Execute and observe** — Triggers the behavior and captures everything:
   - DOM changes
   - Console errors/warnings
   - Network requests (status codes, payloads)
   - JavaScript state (Alpine.js, React, localStorage, hidden inputs)
   - Visual screenshot
4. **Negative verification** — Confirms the behavior does NOT trigger when it shouldn't
5. **Edge case verification** — Rapid actions, browser refresh mid-action, different data states

## Output

A verification report with a clear verdict:

- **CONFIRMED** — Bug reproduced / behavior works as expected
- **NOT REPRODUCED** — Could not trigger the reported issue
- **PARTIALLY VERIFIED** — Some aspects confirmed, others remain unverified
- **REGRESSION FOUND** — Fix introduced a new issue

Includes: exact steps performed, state inspection (DOM + console + network + JS + visual), negative tests, edge cases, confidence level (HIGH/MEDIUM/LOW), and related risks.

## Requirements

- **Playwright MCP server** must be running and configured
- The target web app must be accessible

## Usage Examples

```
/qa-verify auto-save fires on blur
/qa-verify fix for #123
/qa-verify login redirect url:http://localhost:3000
/qa-verify form resets after submit url:http://staging.example.com
```

## Key Principles

- Forensic approach — one thing, tested deeply from every angle
- Always checks all five: DOM + console + network + JS state + visual
- For async operations, inspects network requests rather than just DOM
- Never says "looks good" — states exactly what was observed and why it satisfies criteria
- Clearly states what remains unverified if full verification isn't possible
