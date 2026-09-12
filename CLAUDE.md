# Project: USA Trip (arhab)

Static site (HTML/CSS, no build step) collecting everything for a United
States trip: daily plan, navigation/logistics, and topic research pages
(car rental first). Hosted on **GitHub Pages** from this repo.

- **GitHub repo (remote `origin`)**: https://github.com/avisalmon/arhab.git
- **GitHub Pages URL**: https://avisalmon.github.io/arhab/ (branch `main`, root)
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

- Trip notes doc: https://docs.google.com/document/d/1BXR2ipfOO5Q0voExCE4PzTYwg4jrBsk3/edit?pli=1
- Trip Google My Map: https://www.google.com/maps/d/u/0/edit?mid=1WM9u-u5MO-tDHtt3ySLaDUeo9hJZDwA
- These can't be fetched automatically (auth-gated) — content gets pulled in
  manually/pasted from there into the relevant page as details firm up.

## Python standing rules (from global CLAUDE.md, apply if any scripts are added)

- Virtualenv is always named `env` (already created here) — never `.venv`/`venv`.
- Target it explicitly per command (shell state doesn't persist):
  `.\env\Scripts\python.exe ...` / `.\env\Scripts\pip.exe ...`
- Dependencies go in `requirements.txt`.
- This project currently has no Python logic — it's pure static HTML/CSS —
  so `env`/`requirements.txt` exist per standing setup convention but aren't
  actively used yet.
