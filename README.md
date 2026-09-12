# USA Trip

Planning hub for our United States road trip: daily itinerary, navigation/logistics info, car rental research, and everything else, all in one static site.

## Structure

- [`index.html`](index.html) — home page / menu hub (root, served by GitHub Pages)
- [`pages/`](pages/) — one HTML page per topic (car rental, daily plan, navigation, ...)
- [`css/style.css`](css/style.css) — shared stylesheet for all pages
- [`docs/spec.md`](docs/spec.md) — what this site is meant to cover
- [`docs/backlog.md`](docs/backlog.md) — pages/features still to build

## Run locally

It's static HTML — just open [index.html](index.html) in a browser, or serve the folder:

```bash
python -m http.server 8000
```

Then visit http://localhost:8000/

## GitHub Pages

Served from the `main` branch, root folder, at:
https://avisalmon.github.io/arhab/
