# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static website for "Familie Koch" (content in German), served by **GitHub Pages** at the custom domain **kochts.de** (set via the `CNAME` file). Repo: `github.com/Pawgsy/Kochts`.

## Build / test / deploy

There is **no build system, package manager, or test suite** — no `package.json`, no `Gemfile`, no CI. Despite the Jekyll-oriented `.gitignore`, the site is plain hand-written HTML with no Jekyll front matter, so GitHub Pages serves the files as-is.

- **Preview locally:** open `index.html` directly, or serve the folder (e.g. `python -m http.server`) so root-absolute asset paths resolve.
- **Deploy:** push to `main`. GitHub Pages publishes automatically; `CNAME` (`kochts.de`) sets the custom domain — do not remove it or the domain mapping breaks.

## Architecture notes

- **Everything lives in `index.html`.** Layout styling is in a single inline `<style>` block in the `<head>`; a CSS custom-property palette (`--primary-color`, `--secondary-color`, `--accent-color`, `--background-color`, plus `-rgba` variants) is defined on the `*` selector and used throughout.
- **The page is a skeleton under construction.** The three `<main>` `<section>` elements are empty and have no `id`, while the `#quickscroll` sidebar links to anchors (`#card`, `#tagbox`, `#linkSection`) that don't exist yet — expect to fill these in.
- **Many referenced assets are not in the repo.** `index.html` links `css/style.css`, `css/styles.css`, `css/main.css`, `style.css`, `css/icons.css`, `manifest.json`, and several favicon/logo images that are absent. Broken links here are the current state, not a regression — either add the files or prune the tags.
- **Third-party dependencies are CDN-loaded, not vendored:** Bootstrap 5.3.6 (CSS + JS bundle, with SRI hashes), normalize.css, Meyer reset, and Google Material Symbols Outlined.
- **Cross-site links:** header/footer legal links (Impressum, Datenschutz, Kontakt) point to `links.floko.cc`; the login link points to `login.kochts.de`. These are external and not part of this repo.
