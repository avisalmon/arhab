# Spec — USA Trip site

## Purpose
A single static site (GitHub Pages) that collects everything for our United
States trip: daily plan, navigation/logistics info, and topic research
(starting with car rental). `index.html` is the hub; every topic gets its own
page under `pages/`, linked from the top nav and the home page card grid.

## Pages
- **Home** (`index.html`) — menu hub, links to every topic, quick reference
  to the live external sources.
- **Car Rental** (`pages/car-rental.html`) — what to rent, where, when, cost
  drivers, booking tips. *(first content page)*
- **Daily Plan** (`pages/daily-plan.html`) — day-by-day itinerary.
- **Navigation & Info** (`pages/navigation.html`) — routes, distances, driving
  rules, ID/license requirements, general logistics.
- Future: Lodging, Budget, Packing List (see `backlog.md`).

## Live external sources
- Trip notes Google Doc: https://docs.google.com/document/d/1BXR2ipfOO5Q0voExCE4PzTYwg4jrBsk3/edit?pli=1
- Trip Google My Map: https://www.google.com/maps/d/u/0/edit?mid=1WM9u-u5MO-tDHtt3ySLaDUeo9hJZDwA
- Both require Google sign-in to open, so content gets pulled in manually /
  pasted from there into the relevant page rather than fetched live.

## Design
- Shared stylesheet at `css/style.css`, light/dark aware (respects
  `prefers-color-scheme`).
- Sticky top nav on every page; home page also shows a card grid to each
  topic with a status badge (Ready / Coming soon / Not started).
- Plain HTML/CSS, no build step, no framework — keep it easy to hand-edit.
- **Phone-friendly is a hard requirement** — every page must work well at
  ~375px width (see `CLAUDE.md` for the specific rules: viewport meta,
  `.table-wrap` around every table, no fixed/oversized widths).
