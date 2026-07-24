# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single self-contained static page (`index.html`) presenting Claudia de Luna's NAF Advisory Board submission as an interactive "sealed letter": a wax seal is clicked to open a 3D CSS envelope, revealing the essay, signature, links, and a blog-summary graphic. Deployed to Cloudflare Pages as plain static HTML — **no build step, no framework, no npm, no tests.**

## Running / previewing

Open `index.html` directly in a browser, or serve the folder statically:

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

Deployment: Cloudflare Pages (drag-and-drop upload, or Git-connected to `main` with framework preset `None`, blank build command, root output dir). See `README.md` for full deploy steps.

## Architecture

Everything lives in `index.html` — CSS is in a single `<style>` block in `<head>`, markup in `<body>`, and a small vanilla-JS `<script>` at the end. There are no external dependencies except Google Fonts (Cormorant Garamond + Inter).

The interaction is entirely CSS-driven off one state class: JS toggles `.open` on `#envelope` (and `.hidden` on the seal). All animation — flap rotating, letter sliding up and fading in, falling petals — is defined as CSS transitions/keyframes that react to that class. To change animation behavior, edit the CSS rules under `.envelope.open ...`, not the JS.

Key layered pieces inside `.stage` (a `perspective` container), stacked by `z-index`:
- `.envelope` — `transform-style: preserve-3d` container sized in `vw`; its `.base/.side/.front/.flap` panels are `clip-path` polygons forming the envelope shape.
- `.letter` — the paper, absolutely positioned, hidden below the envelope until `.open` slides it up. Content scrolls inside `.letter-scroll`.
- `.seal` — the clickable wax button, hidden on open.

### Layout gotcha: envelope vs. letter width

The envelope and the letter are sized independently (`.envelope` width vs `.letter` width, each with its own value in the base rules **and** in the `@media (max-width: 900px)` and `720px` blocks). If the letter looks narrow / graphics look "smushed" relative to a wide envelope, it's because the letter's `min(…vw, …px)` cap is much smaller than the envelope's. Keep the two proportional across **all three** breakpoints when adjusting either.

## Assets

Images live in `assets/` and are referenced with exact filenames from `index.html`. The referenced names must match the files on disk exactly (case-sensitive, including extension) or they render as broken images on Cloudflare. Note the repo currently contains extra/variant image files (e.g. `.png` vs `.jpg`, `Signature.png`) — confirm the `src` in `index.html` points at a file that actually exists before deploying.
