# qa-plan

**Command:** `/qa-plan [feature | from:<discovery-report-path>]`

## Purpose

Generates a comprehensive, structured test plan with exact steps, test data, and expected results. Produces test cases specific enough that a human or AI tester can execute them **without ambiguity**.

## What It Does

Takes input from a QA discovery report, a feature name, or auto-scans the project, then generates test cases across **10 categories**:

1. **Happy Path** — Standard successful flows
2. **Validation** — Every field with every invalid input type
3. **Boundary** — Min, max, just-under, just-over for limits
4. **State** — Different starting states (empty, partial, full, error)
5. **Negative** — Missing required fields, wrong types, expired sessions
6. **Integration** — Data flows between components
7. **Concurrency** — Rapid clicks, duplicate submissions, race conditions
8. **Security** — XSS, injection, unauthorized access, CSRF
9. **Accessibility** — Keyboard navigation, screen reader, focus management
10. **Responsive** — Mobile, tablet, desktop viewport behavior

### Test Data Strategy

For every input field, generates exact values:
- Valid value, empty, too long, special characters
- SQL injection: `'; DROP TABLE--`
- XSS: `<script>alert(1)</script>`
- Numerics: min, max, zero, negative, decimal, NaN
- Dates: past, future, today, invalid format, leap year

## Output

A structured test plan including:
- Summary with counts by priority (P0-P3) and category
- Test data setup requirements
- Individual test cases with: preconditions, exact steps, exact expected results, CSS selectors
- Traceability matrix (business rule -> test cases -> coverage)
- Gaps and risks

## Usage Examples

```
/qa-plan                              # Auto-discover and plan
/qa-plan from:qa-discovery-report.md  # Plan from discovery output
/qa-plan feature:login                # Plan for specific feature
```

## Key Principles

- Every validation rule must have at least one test case
- Every user story must have happy-path AND negative test cases
- No placeholders — uses exact values like `test@example.com`, not "enter a valid email"
- Cross-references every test case to its source business rule
