# qa-execute

**Command:** `/qa-execute <base-url> [plan:<path> | feature:<name> | module:<N>]`

## Purpose

Executes QA test cases against a **live web application** using Playwright MCP browser tools. This skill navigates pages, fills forms, clicks buttons, takes screenshots, and reports exactly what it observes — like a human tester with a browser.

## What It Does

- **With a test plan** (`plan:path.md`) — Reads the plan and executes each test case step-by-step
- **With a feature** (`feature:login`) — Focuses testing on that specific feature
- **URL only** — Performs exploratory testing: navigates the app, finds features, tests happy paths, tries invalid data, checks error handling

### Browser Actions Available

Navigate, snapshot DOM, click, type, fill forms, select dropdowns, press keys, upload files, scroll, wait for elements, take screenshots, read console logs, inspect network requests, and evaluate JavaScript.

### Execution Protocol

For each test:
1. Navigate to starting URL + snapshot + screenshot (baseline)
2. Execute steps, snapshotting after every state change
3. After form submissions: wait for response, check network calls, check console for errors
4. Record PASS / FAIL / BLOCKED with evidence

## Output

A test execution results table per test suite:

| # | Test Case | Action | Expected | Actual | Status | Screenshot |
|---|-----------|--------|----------|--------|--------|------------|

Plus console error audit, network issue audit, and bugs found with severity.

## Requirements

- **Playwright MCP server** must be running and configured
- The target web app must be accessible at the provided URL

## Usage Examples

```
/qa-execute http://localhost:3000
/qa-execute http://localhost:9174 plan:test-plan.md
/qa-execute http://staging.example.com feature:login
```

## Key Principles

- Never assumes page content — always snapshots first
- Never fabricates results — reports "UNABLE TO VERIFY" if it can't confirm
- Takes screenshots liberally as evidence
- Zero tolerance for JS console errors
- Asks user before destructive actions (delete, deploy, payment)
