# CLAUDE.md — CommerceLab Presentation Standards

This file defines how every presentation in this repository is built so that all decks
stay consistent, on-brand, and indistinguishable from professionally hand-crafted
corporate material. **Read this before creating or editing any deck.**

---

## 0. Golden rules

1. **Never let it feel AI-generated.** No emoji, no generic "leverage synergies" filler,
   no rainbow gradients, no clip-art, no over-symmetrical bullet soup. Write like a senior
   strategist: specific, confident, sparing. Vary sentence and slide rhythm.
2. **One presentation = one GUID folder.** Folder name is a v4 UUID. This is the access key.
3. **Self-printing to PDF.** Every deck must export cleanly as one slide per page via the
   browser print dialog — no manual fixing.
4. **Shared theme.** All visual styling lives in `assets/theme.css`. Decks contain content
   only; they do not redefine the design system.
5. **Push to GitHub Pages when done.** Remote: `https://github.com/commercelabtr/cl-presentations`.

---

## 1. Brand identity

| Token | Value | Use |
|-------|-------|-----|
| Ink | `#1A1A1A` | Primary text, dark slides, footer brand |
| Signal red | `#D02C2F` | Accent only — kickers, key words, ticks, one node per diagram |
| Red (deep) | `#A81F22` | Hover / pressed states |
| Paper | `#FFFFFF` | Light slide background |
| Bone | `#F6F4F0` | Card backgrounds |
| Muted | `#6C6A66` | Secondary text |
| Line | `#E4E1DA` | Hairlines, card borders |

- Logo: `assets/commercelab-logo.svg` (dark slides use `commercelab-logo-white.svg`).
- **Red is a scalpel, not a paint roller.** Use it to draw the eye to *one* thing per slide.
- Fonts: **Manrope** (display/headings, 700–800), **Inter** (body, 400–600). Loaded from
  Google Fonts in each deck's `<head>`. Newsreader is available as an optional serif.

## 2. Canvas & layout

- Slides are a fixed **16:9** canvas. Typography is sized in **container-query units
  (`cqw`/`cqh`)** so everything scales identically on screen and in print. **Never use `px`
  for slide content** — only `cqw`/`cqh` (px is allowed only in the off-canvas toolbar).
- Print target: `@page { size: 1280px 720px; margin: 0 }`, one `.slide` per page. Already
  handled by `theme.css`; do not override.
- Every slide uses this skeleton:

```html
<section class="slide">            <!-- add slide--ink for dark/section/cover slides -->
  <div class="slide__inner">
    <span class="kicker">Section label</span>
    <h2 class="slide-title">Headline with one <span class="accent">red</span> word</h2>
    <!-- content: .lead, .grid + .card, .flist, .flow, .stack, .stat-row ... -->
  </div>
  <div class="slide__footer">
    <span class="brand"><img src="../assets/commercelab-logo.svg" alt="" /></span>
    <span class="conf">Confidential</span>
    <span class="slide__no">NN / TT</span>
  </div>
</section>
```

- Dark slides (`slide--ink`) must use `commercelab-logo-white.svg` in the footer.

## 3. Component vocabulary (in `theme.css`)

- `.kicker` — uppercase red section label with a leading rule. One per slide, above the title.
- `.slide-title` — Manrope 800 headline. Wrap **at most one phrase** in `.accent` (red).
- `.lead` — one-sentence muted intro under the title (optional).
- `.grid` + `.grid-2/3/4` with `.card` — feature/concept grids. Variants: `.card--accent`
  (red left border), `.card--dark` (ink background, for one emphasis card), `.card .ix`
  (small red index/label).
- `.flist` — bullet list with red square ticks; `<b>` the lead term of each item.
- `.flow` — horizontal pipeline of `.node` boxes with `&rarr;` arrows. Use `.node--red`
  for the single focal step, `.node--ink` for the terminal step. Optional `<small>` subtitle.
- `.stack` + `.layer` — vertical layered architecture diagram; `.layer--ink` for the
  orchestration/emphasis layer; `.layer .tag` is the red rail label.
- `.stat-row` + `.stat` (`.num` red, `.lab` muted) — metrics.
- `.pill` / `.pillrow` — tag chips.
- Section dividers and cover: `slide--ink`; cover/closing add `slide--cover`; section
  dividers use `.divider-index` (big roman numeral).

## 4. Deck structure (default narrative arc)

1. Cover (ink).
2. Company / what it is + vision & mission.
3. Positioning / differentiators.
4. Market or solution landscape.
5. Architecture or product overview.
6. Proof — metrics / outcomes.
7. Numbered **section dividers** (ink) between major parts; keep ~6–10 content slides each.
8. Closing slide (ink) with contact: Windowist Tower, Maslak — İstanbul ·
   info@commercelab.com.tr · +90 212 214 73 90.

Keep slides to **one idea each**. 3–6 cards, or 4–6 flist items, max. If it's crowded,
split it. Footer numbering is `NN / TT` (total) — update **all** footers when slide count changes.

## 5. Language & tone

- **Default language: English** (matches CommerceLab's brand materials and an investor
  audience). Switch to Turkish only when the audience requires it; keep one language per deck.
- Sentence case for body, not Title Case. No trailing exclamation marks. Numbers and ranges
  beat adjectives ("+35% efficiency" > "hugely efficient").
- Source of truth for product facts: `Commerce_Lab 2025 v1.pdf` and commercelab.com.tr.
  Technical-architecture facts are grounded in the real stack (.NET / C#, PostgreSQL,
  MongoDB, Redis, RabbitMQ, Elasticsearch, GraphQL, Docker/Kubernetes/AWS, multi-tenant,
  rule/state/event engines, plugins). Do not invent metrics — cite the deck/PDF ranges.

## 6. Export to PDF

Browser print → Landscape, margins **None**, **Background graphics ON**. Each slide
prints as one full page automatically. The on-screen "Download PDF" button triggers this.

## 7. Publishing workflow

```bash
python3 -c "import uuid; print(uuid.uuid4())"   # new deck folder name
# build <guid>/index.html using ../assets/theme.css
git add -A && git commit -m "Add <topic> presentation"
git push
```

GitHub Pages: deploy from `main` branch, root. `.nojekyll` keeps all folders served as-is.
Decks are public-but-unlisted — never add a deck index to `index.html` or the README.

## 8. Inventory of decks

| GUID | Topic | Audience | Date |
|------|-------|----------|------|
| `1ffeab01-f6f7-4a79-a64b-bc001da4dda1` | Platform & infrastructure overview | Investor | 2025 |
