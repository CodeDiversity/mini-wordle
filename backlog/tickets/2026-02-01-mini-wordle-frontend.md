---
title: Frontend — grid, input, keyboard
type: feature
priority: high
estimate: 2d
created: 2026-02-01
---

### Description
Implement the React UI components for the Mini-Wordle grid, tile, and keyboard. Handle keyboard and physical keyboard input, submit guesses to the engine, display coloring per tile, and show win/lose modals. Support selecting 3- or 4-letter game length at game start.

### Acceptance criteria
- Grid renders correct columns for selected length and 6 rows for attempts.
- On-screen keyboard updates letter states (gray/yellow/green) as guesses are evaluated.
- Physical keyboard input and on-screen keyboard work (Enter submits, Backspace deletes).
- Win and lose states are displayed with the correct solution.
- Basic responsive layout and minimal accessible labels.

### Test plan
- Component unit tests (Vitest + React Testing Library) for tile rendering and keyboard interactions.
- Manual playthrough in browser verifying input and visual feedback.
