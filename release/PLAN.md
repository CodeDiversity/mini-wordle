# Mini-Wordle Release Plan (MVP)

Date: 2026-02-01

## Objective
Build a compact, single-player Wordle-like web game for 3–4 letter words with the standard Wordle feedback loop and 6 guesses.

## Goals
- Fast, friendly UI for quick play sessions
- Correct, well-tested game engine (duplicate-letter rules handled)
- Small curated wordlists for 3- and 4-letter games
- Simple, accessible frontend (React + Vite + TypeScript per AGENTS.md)

## MVP scope
- Playable single-player web app
- Support guessing 3- or 4-letter words (length selector at game start)
- 6 tries per game
- Color feedback: green (right spot), yellow (in word wrong spot), gray (absent)
- On-screen keyboard reflecting letter states
- Basic responsive styles and keyboard input handling
- Unit tests for core game logic (Vitest)

## Out of scope (post-MVP)
- Multiplayer, accounts, analytics
- Advanced UI polish and animations (nice-to-have)
- Cross-device build optimization beyond responsive CSS

## Acceptance criteria
- Game engine exposes a small API to evaluate guesses and returns per-letter states
- UI allows typing, submitting, shows grid and keyboard, and ends with win/lose screens
- Wordlist integrated and validated
- Unit tests cover core game logic and duplicate-letter edge cases

## Risks & mitigation
- Wordlist quality: curate and add tests that validate uniqueness and simplicity.
- Duplicate-letter handling: include thorough unit tests and sample cases.

## Implementation slices
1. Core game engine + unit tests — small, deterministic module that evaluates guesses
2. Frontend UI: grid, tile, keyboard, input handling, and end-game states
3. Wordlist: curate lists for 3- and 4-letter words and add validation tests

## Next 3 items (highest priority)
- Implement and land core game engine + unit tests (`backlog/tickets/2026-02-01-mini-wordle-mvp.md`)
- Implement front-end input + grid and wire to engine (`backlog/tickets/2026-02-01-mini-wordle-frontend.md`)
- Add and validate curated 3/4-letter wordlists (`backlog/tickets/2026-02-01-mini-wordle-wordlist.md`)

## How we'll verify
- Run unit tests (Vitest) for the engine
- Manual playthroughs for both 3- and 4-letter modes
- Lint and typecheck per repo rules before merging

## Owners
- Coordinator: project owner (assign in PR)
- Implementation: frontend + api implementers (per AGENTS.md)

