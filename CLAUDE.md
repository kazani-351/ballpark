# CLAUDE.md — ballpark

Static single-file browser game. No build, no deps, no backend.

## Layout
- `index.html` — the whole app (inline CSS + JS).
- `favicon.svg` — app mark.
- `og-image.png` — social card (1200×630).

## Run / verify
- Open `index.html` directly, or `python3 -m http.server` then visit it.
- Verify by playing: free play in each mode, plus the daily challenge.
- Daily must be deterministic: same UTC date → identical numbers on reload.

## Conventions
- Keep it a single self-contained `index.html`. No frameworks, no bundler.
- `localStorage` keys are namespaced `ballpark.*`.
- Difficulty config lives in the `MODES` object; daily uses `DAILY_MODE = 'normal'`.
- Determinism: free play may use `Math.random`; the daily challenge must only use
  the seeded `mulberry32` stream and `pickNFixed` (screen-independent).

## Git
- Branch `build`. Push only on explicit instruction. No secrets expected.
