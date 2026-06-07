# ballpark

A minimalist game of numerical intuition. A number appears above a `0 to N`
line — click where you think it falls. Scored by how far off you are (% of range).

A fork of the "eyeball" estimation game, rebuilt and extended with:
- **Difficulty modes** — easy / normal / hard (tune range size + grading, separate stats).
- **Game modes** — classic, **world** (place a real-world fact), **reverse** (read the
  marker, type the number), **survival** (one miss ends the run).
- **Daily challenge** — 5 fixed, date-seeded rounds, identical for everyone that local
  day. Wordle-style emoji share + **day streak**, plus a local-midnight countdown and an
  "already played today" badge. Share generates a PNG card (Web Share / download).
- **Light + dark** theme (syncs the browser `theme-color`).
- A retuned minimal look. `og-image.png` (1200×630) for link unfurls.

## Run

No build step. It's a single static file.

```
open index.html          # macOS
# or serve it:
python3 -m http.server    # then visit http://localhost:8000
```

## How it works

- `index.html` — the entire app (inline CSS + JS, no dependencies).
- Stats persist in `localStorage`, namespaced `ballpark.*`, separate per mode.
- The daily challenge seeds a `mulberry32` PRNG from the UTC date, so numbers are
  screen-independent and the same worldwide. Rolls over at UTC midnight.
- `favicon.svg` — line-and-marker mark.
- `og-image.png` — 1200×630 social card.

## Deploy

Static host (Cloudflare Pages / GitHub Pages). The share URL auto-uses
`location.origin`; the placeholder fallback `https://ballpark.pages.dev` is only
used when opened as a local file.
