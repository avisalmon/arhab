# Project: USA Trip (arhab)

Static site (HTML/CSS, no build step) collecting everything for a United
States trip: daily plan, navigation/logistics, and topic research pages
(car rental first). Hosted on **GitHub Pages** from this repo.

- **GitHub repo (remote `origin`)**: <https://github.com/avisalmon/arhab.git>
- **GitHub Pages URL**: <https://avisalmon.github.io/arhab/> (branch `main`, root)
- This session/repo is the single source of truth — always commit and
  **push to `origin main`** after making changes here, so the user can see
  updates and set/adjust GitHub Pages on their end.

## Standing requirement: phone-friendly, always

**Every page must work well at phone width (~360–430px), not just desktop.**
This is a hard requirement, not a nice-to-have — check it whenever adding or
editing a page:

- `viewport` meta tag on every page: `width=device-width, initial-scale=1.0`.
- Use the shared `css/style.css` — it already handles this (fluid `.wrap`
  container with side padding, `card-grid` that collapses to one column,
  nav that wraps, a `<480px` tightening media query). Don't fight it with
  inline widths or fixed pixel layouts.
- **Any `<table>` must be wrapped** in `<div class="table-wrap">...</div>`
  so it scrolls horizontally on narrow screens instead of breaking the
  page layout (see `.table-wrap` in `css/style.css`).
- No fixed-width elements wider than the viewport; no `min-width` wider
  than ~400px anywhere; images/media need `max-width: 100%` (already the
  default via the CSS reset for images).
- Test new pages by mentally checking (or actually resizing) at ~375px
  width before considering a page done.

## Structure

- `index.html` — home/menu hub (repo root, required by GitHub Pages)
- `pages/*.html` — one page per topic (`car-rental.html`, `daily-plan.html`,
  `navigation.html`, more to come — see `docs/backlog.md`)
- `css/style.css` — single shared stylesheet for every page (light/dark
  aware via `prefers-color-scheme`)
- `docs/spec.md` — what the site covers
- `docs/backlog.md` — what's built vs. still to do

## Live external sources (not in this repo, require Google sign-in)

- Trip notes doc: <https://docs.google.com/document/d/1BXR2ipfOO5Q0voExCE4PzTYwg4jrBsk3/edit?pli=1>
- Trip Google My Map: <https://www.google.com/maps/d/u/0/edit?mid=1WM9u-u5MO-tDHtt3ySLaDUeo9hJZDwA>
- **Neither is fetchable automatically** — confirmed 401 Unauthorized on the
  view, `/export?format=txt`, and `/pub` endpoints, and no Google Docs/Drive
  MCP connector is available in this environment (only Gmail is connected).
  Do not re-attempt auto-fetching these; use the ground-truth workflow below.

### Ground-truth sync workflow (the trip notes doc is source of truth)

Avi's Google Doc is the group's ground truth for trip details (group size,
route, dates, sleeping arrangements, etc. — written in Hebrew). Since it
can't be pulled live, the flow is export → convert → sync:

1. Avi exports it from Google Docs as **.docx** (File → Download → Microsoft
   Word (.docx)) and drops/overwrites it at **`docs/source-trip-notes.docx`**.
2. Convert it to Markdown with the project's `env` virtualenv:
   `.\env\Scripts\python.exe scripts\docx_to_md.py docs\source-trip-notes.docx docs\source-trip-notes.md`
   This walks the doc body in order (paragraphs + tables interleaved, not
   python-docx's default separated collections) so the output reads the same
   order as the original doc. `docs/source-trip-notes.md` is generated —
   don't hand-edit it beyond the one-off header cleanup already done; re-run
   the script after every re-export instead.
3. Read `docs/source-trip-notes.md` and use it to update the relevant site
   pages (Daily Plan, Navigation, Car Rental, etc.) — it is the authoritative
   source, in Hebrew; keep names/places/times faithful to it and translate
   only what's needed for page structure, not the substance.
4. If the site pages reference details not in the current
   `docs/source-trip-notes.md`, or Avi mentions the doc changed, ask him to
   re-export rather than guessing or re-attempting a live fetch.

Current trip shape (from the first sync, 2026-09-18 → 2026-10-02): family of
5 (Nirit, Avi + sons), flights UA85 (EWR arrival) / UA84 (EWR departure),
route NYC (4 nights Manhattan) → Finger Lakes (Geneva) → Niagara Falls
(Canadian side) → Leonard Harrison SP / Lancaster → Amish + DC (2 nights) →
Philadelphia + Atlantic City (2 nights) → New Jersey (2 nights) → fly home.
Treat this summary as a quick orientation only — always defer to the current
`docs/source-trip-notes.md` for exact details.

## Python standing rules (from global CLAUDE.md, apply if any scripts are added)

- Virtualenv is always named `env` (already created here) — never `.venv`/`venv`.
- Target it explicitly per command (shell state doesn't persist):
  `.\env\Scripts\python.exe ...` / `.\env\Scripts\pip.exe ...`
- Dependencies go in `requirements.txt`.
- This project currently has no Python logic — it's pure static HTML/CSS —
  so `env`/`requirements.txt` exist per standing setup convention but aren't
  actively used yet.
