---
title: Mini-Wordle — core game engine
type: feature
priority: high
estimate: 1.5d
created: 2026-02-01
---

### Description

Implement the core deterministic game engine that selects a target word (3 or 4 letters), accepts guesses, enforces the 6-guess limit, and returns per-letter statuses: correct (green), present (yellow), absent (gray). Must handle duplicate-letter rules consistent with Wordle.

### Acceptance criteria

- Exported function (e.g. `evaluateGuess(target, guess)`) returns an array of per-letter states: `correct|present|absent`.
- Correct handling of duplicate letters according to Wordle rules.
- Unit tests (Vitest) cover typical and edge cases (duplicates, all-correct, all-absent, mixed).
- Target selection mechanism (round-robin or seeded PRNG) available for deterministic tests.

### Test plan

- Add unit tests that assert returned states for a matrix of target/guess pairs (include duplicates).
- Manual harness to run the engine from the console during development.

### Notes

- Keep API minimal and typed (TypeScript).
- Add JSON wordlists later and a selector function.
