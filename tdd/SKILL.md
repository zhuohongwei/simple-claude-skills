---
name: tdd
description: Enforce TDD cycle (stub → red tests → green implementation → refactor) when implementing new testable business logic
---

# TDD Workflow

Follow this cycle for all testable business logic. Do not implement logic and tests in the same tool call.

## Phase 1: Stub (Red)

1. Define function signatures in the target file
2. Body must be only: `throw new Error('Not implemented')`
3. Run `pnpm type-check` — must pass

## Phase 2: Test (Red)

1. Write tests targeting the stubs
2. Run `pnpm test`
3. **Gate:** Tests must compile and FAIL with "Not implemented" error. Do not proceed if tests pass or have compilation errors.

## Phase 3: Implement (Green)

1. Replace stubs with actual business logic
2. Run `pnpm test`
3. **Gate:** All tests must pass

## Phase 4: Refactor

1. Review for DRY and architectural alignment
2. Run `pnpm test` — confirm no regressions

## Rules

- If asked to "Implement X," your first response must be stubs + tests, not the solution
- Each phase is a separate tool-call turn — never combine stub creation with implementation
- If tests pass during Phase 2, your stub is wrong (it should throw)
- If tests fail during Phase 3, fix the implementation before proceeding