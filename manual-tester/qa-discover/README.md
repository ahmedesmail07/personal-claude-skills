# qa-discover

**Command:** `/qa-discover [path-or-module]`

## Purpose

Performs requirements extraction and business logic discovery by reading the actual codebase. This is the **first step** in the QA workflow — before you can test anything, you need to know what the application does.

## What It Does

1. **Architecture Scan** — Identifies the framework, entry points (routes, APIs, pages), and data flow (models -> services -> views -> templates).

2. **Business Logic Extraction** — For every feature/module it finds:
   - **Validation rules** — form validators, model constraints, API input checks, DB constraints
   - **Conditional business rules** — branching logic, feature flags, permission checks, state machines
   - **Data relationships** — foreign keys, cascade behavior, uniqueness constraints
   - **Edge cases already handled** — existing try/catch blocks, fallback values, retry logic

3. **User Story Generation** — Translates discovered behavior into structured user stories with acceptance criteria (GIVEN/WHEN/THEN format).

4. **Testability Assessment** — Rates each story on: automatable? already tested? risk level? complexity?

## Output

A structured **QA Discovery Report** including:
- Architecture summary
- Business logic map with file paths and line numbers
- User stories with acceptance criteria
- Cross-cutting concerns (auth, error handling, auto-save)
- High-risk untested areas
- Recommended test priority

## Usage Examples

```
/qa-discover                    # Analyze entire project
/qa-discover src/auth           # Focus on auth module
/qa-discover apps/billing       # Focus on billing app
```

## Key Principles

- Reads actual code — never guesses from file names
- Includes file paths and line numbers for every rule
- Flags contradictions (e.g., client says required, server says optional)
- Flags silent failures (catch-all handlers that swallow errors)
