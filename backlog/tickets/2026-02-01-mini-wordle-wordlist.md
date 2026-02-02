---
title: Wordlist — curate 3- and 4-letter wordlists
type: task
priority: high
estimate: 0.5d
created: 2026-02-01
---

### Description
Create and validate two small curated wordlists: one for 3-letter words and one for 4-letter words. Lists should prefer common, easy words and exclude proper nouns, abbreviations, and offensive content. Provide lists as `data/words-3.json` and `data/words-4.json` or a TS module.

### Acceptance criteria
- Wordlists exist in `data/` as JSON or TS module.
- All words are lowercase, alphabetical, and unique.
- Tests that validate list constraints (length, uniqueness, allowed characters).

### Test plan
- Add unit tests that load each list and assert constraints.

### Notes
- Keep lists intentionally small (200–1000 words depending on desired difficulty). Start small and expand if needed.
