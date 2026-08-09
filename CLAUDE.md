# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Sitzprobe: an interactive 3D seat-preview concept demo for opera houses/theatres, loosely modeled on Opernhaus Graz. Click a seat in the Parkett, Logen (boxes), or Galerie and the camera flies into that seat's own point of view, so you can see what the seat actually sees before booking. Personal portfolio/concept demo, not affiliated with Opernhaus Graz. This nested folder is the actual git repo (origin `ozbayemrah/OperGrazSitzProbe`); the parent `OperGraz/` folder is not itself a repo.

## Running it

No build step or server needed — open `index.html` directly in a browser (Three.js r128 is loaded classic/non-module from a CDN so it works over `file://`).

## Architecture notes

- Everything (markup, CSS, JS) is in one `index.html`. The auditorium is procedurally generated from parameters near the top of the `<script>` block (`TIERS` for tier colors/prices, `buildTierSeats()` for row counts/radii/spacing, `addTierFacade` for the hall shell) — no 3D models, just primitive geometry, instanced for ~1,000+ seats.
- Seat click → POV flight: `onClick` raycasts against the instanced seat meshes to find the clicked seat, then sets `isFlying = true` and animates the camera to that seat's position/look-at-stage orientation; once arrived, `inPOV = true` locks the camera to that seat while still allowing free look-around (drag) without changing position. `backToOverview` reverses this.
- Seats marked `sold` render grayed out and show a toast on click instead of flying in.
