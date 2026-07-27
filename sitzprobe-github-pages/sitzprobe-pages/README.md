# Sitzprobe

**See your seat before you book.** A concept demo of an interactive 3D seat‑preview tool for opera houses and theatres — loosely inspired by the layout of the **Opernhaus Graz**. Click any seat in the Parkett, a tier of Logen, or the Galerie to fly into that seat's own point of view and see exactly what you'd see from there, including realistically restricted sightlines from side boxes.

**[View the live demo](#)** ← replace with your GitHub Pages URL once deployed (see below)

## What this is

- A single self‑contained `index.html` — no build step, no dependencies to install.
- A procedurally generated 3D auditorium (Three.js) with instanced seating (~1,200+ seats), first‑person seat POV, sold/available seat states, and a bilingual (DE/EN) interface.
- **A concept/portfolio demo only.** It is not affiliated with, endorsed by, or built from any non‑public materials belonging to Opernhaus Graz, Bühnen Graz, or any ticketing provider. No real tickets, pricing, or availability data are used — everything is placeholder/synthetic.

## Features

- Click‑to‑seat first‑person camera flight, with free look‑around from the seat
- Procedurally generated horseshoe hall (Parkett, Logen, Galerie) with balcony rails
- Sold‑out seats shown grayed out, with a toggle to show only available seats
- Restricted‑sightline flagging for side boxes
- German / English language switch
- Runs entirely client‑side; works when opened directly from disk or hosted statically

## Running locally

Just open `index.html` in a browser — no server or build step required.

## Deploying to GitHub Pages

1. Create a new GitHub repository and push these files (`index.html`, `.nojekyll`, `README.md`) to the `main` branch.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
4. Choose branch `main` and folder `/ (root)`, then **Save**.
5. GitHub will publish the site at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

The included `.nojekyll` file tells GitHub Pages to serve the site as-is, skipping Jekyll processing (not strictly required here, but a safe default for a plain static page).

## Tech

- [Three.js](https://threejs.org/) r128 (classic/global build, loaded from cdnjs) + OrbitControls (loaded from jsDelivr)
- Vanilla JavaScript, HTML, CSS — no framework, no bundler
- Google Fonts (Cormorant Garamond, Inter) loaded via `<link>`

## License / attribution

This code is original and was written for this demo; you're free to license it however you'd like once it's in your own repository (e.g. add a `LICENSE` file with MIT if you want it open source). The general "click a seat → fly into its point of view" concept was inspired by an existing open project (a football-stadium seat-view demo), which is separately licensed under PolyForm Noncommercial — this project shares no code with it, but if you build on that project directly elsewhere, note its license restricts commercial use.
