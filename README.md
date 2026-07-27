# Sitzprobe

**See your seat, before you book.**

A concept demo of an interactive 3D seat‑preview tool for opera houses and theatres — loosely inspired by the layout of the **Opernhaus Graz** (Graz Opera). Click any seat in the Parkett, a tier of Logen, or the Galerie and fly straight into that seat's own point of view, so you know exactly what you'll see (and how much a side box's rail blocks) before you buy.

### 🎭 [Live demo](https://ozbayemrah.github.io/OperGrazSitzProbe/)

*(Optional: add a screenshot of the overview or seat-POV to a `docs/` folder and reference it here with `![Sitzprobe](docs/screenshot.png)` once you have one.)*

---

## Why

Ticketing for most mid-size opera and theatre houses still shows a flat 2D seating chart — you find out whether a Loge rail blocks half the stage only after the curtain goes up. Sitzprobe is a proof of concept for a lightweight, no-backend seat-preview layer that any venue could bolt onto an existing ticketing flow: pick a seat, see the real view, then buy with confidence.

## Features

- **Click-to-seat camera flight** — clicking any seat flies the camera directly to that seat's eye level, looking at the stage.
- **Free look-around from your seat** — drag to look up at the chandelier, sideways at neighboring boxes, etc., without breaking the fixed seat position.
- **Procedurally generated horseshoe hall** — Parkett (stalls), three tiers of Logen (boxes), and a Galerie, all instanced for performance (1,000+ seats).
- **Realistic restricted sightlines** — seats in the far side of a box are flagged as having a partially obstructed view, same as in a real Ranglogentheater.
- **Sold vs. available seats** — a portion of seats render grayed out as "sold"; clicking one shows a toast instead of navigating. A legend toggle lets you filter to show only available seats.
- **Bilingual UI** — German / English switch in the top bar, fully live (including the seat panel and tooltips).
- **Zero build step** — one self-contained `index.html`. No npm install, no bundler, no backend.

## Tech stack

- [Three.js](https://threejs.org/) r128 — classic (non-module) global build, loaded from a CDN so the file works even opened directly from disk (`file://`), not just when served
- [OrbitControls](https://threejs.org/docs/#examples/en/controls/OrbitControls) (r128-compatible build)
- Vanilla JavaScript / HTML / CSS — no framework, no bundler, no dependencies to install
- [Google Fonts](https://fonts.google.com/) (Cormorant Garamond, Inter)

## Project structure

```
.
├── index.html      # the entire app — markup, styles, and JS in one file
├── .nojekyll       # tells GitHub Pages to skip Jekyll processing
├── LICENSE         # MIT license
└── README.md
```

## Running locally

No server or build step needed — just open `index.html` in a browser.

```bash
git clone https://github.com/ozbayemrah/OperGrazSitzProbe.git
cd OperGrazSitzProbe
open index.html   # or double-click it, or drag it into a browser tab
```

## Deploying to GitHub Pages

1. Push this repo to GitHub (make sure `index.html` sits at the **root** of the branch you deploy — not inside a subfolder).
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
4. Choose branch `main`, folder `/ (root)`, then **Save**.
5. Your site will publish at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

If the page 404s or looks unstyled after deploying, double check `index.html` is at the repo root and the repo is public (private repos need GitHub Pro/Team/Enterprise for Pages).

## Adapting this for a different venue

The whole auditorium is generated from a handful of parameters near the top of the `<script>` block — tier count, seat rows, radii, pricing, and colors. To reshape it for a different hall type (a cinema's raked rectangular rows, a smaller black-box theatre, a different opera house's proportions), you mainly need to adjust:

- `TIERS` — tier keys, colors, and prices
- `buildTierSeats()` — row counts, base radius, row spacing per tier
- The hall shell / balcony ring geometry (`addTierFacade`, stage/proscenium dimensions)

No 3D modeling tool required — it's all primitive geometry (boxes, cylinders, a torus) generated in code.

## Disclaimer

This is a **personal concept/portfolio demo**, not an official product. It is not affiliated with, endorsed by, or built using any non-public materials from Opernhaus Graz, Bühnen Graz, or any ticketing provider. All prices, showtimes, and seat availability shown are placeholder/synthetic data — no real tickets are sold or represented here.

## License

Released under the [MIT License](./LICENSE) — free to copy, modify, and reuse, commercially or otherwise, with attribution. See the `LICENSE` file for the full text.

## Credits

Created by **Emrah Özbay**.

If you find this useful or want to see more like it, following along means a lot:

- LinkedIn: [linkedin.com/in/ozbayemrah](https://www.linkedin.com/in/ozbayemrah/)
- Behance: [behance.net/ozbayemrah](https://www.behance.net/ozbayemrah)
