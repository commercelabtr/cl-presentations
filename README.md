# CommerceLab Presentations

Corporate presentation decks for CommerceLab, published as static HTML on GitHub Pages.

## Structure

- `assets/` — shared brand theme (`theme.css`) and logos.
- `<guid>/index.html` — one presentation per GUID-named folder. The GUID acts as an
  unguessable access key: only people who have the link can reach a deck.
- `index.html` — neutral landing page (no deck listing, by design).

## Access model

Decks are **public but unlisted**. There is no index of presentations anywhere in the
repo or site. A deck is reachable only via its full GUID URL, e.g.

```
https://commercelabtr.github.io/cl-presentations/<guid>/
```

Pages are also marked `noindex, nofollow` so search engines do not list them.

## Viewing & exporting to PDF

Open a deck in a browser. Use the **Download PDF** button (or `Cmd/Ctrl + P`) and print
to PDF. Each slide is laid out as one 16:9 page (1280×720), so the export is one
slide per page with no manual adjustment. Recommended print settings: landscape,
margins **None**, **Background graphics ON**.

Use arrow keys / Page Up / Page Down to navigate on screen.

## Adding a new presentation

1. Generate a GUID: `python3 -c "import uuid; print(uuid.uuid4())"`.
2. Create `<guid>/index.html` referencing `../assets/theme.css` and the logos.
3. Follow the standards in `CLAUDE.md` to keep every deck on-brand and consistent.

## Publishing

GitHub Pages serves the `main` branch root. `.nojekyll` is present so all folders are
served as-is.
