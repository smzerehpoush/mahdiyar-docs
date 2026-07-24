# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static site of work documents and presentation slide decks (in Persian/Farsi), published automatically to GitHub Pages at `https://smzerehpoush.github.io/mahdiyar-docs/`. There is no build step, no dependencies, no tests — every page is a single self-contained HTML file with inline CSS and JS.

## Development

Open `index.html` (or any file in `decks/`) directly in a browser. Pushing to `main` triggers `.github/workflows/pages.yml`, which deploys the repo root as-is to GitHub Pages.

## Structure and conventions

- `index.html` — landing page listing all decks as cards.
- `decks/*.html` — one standalone HTML file per deck.

Adding a new deck is a two-step change: create the HTML file in `decks/`, then add a matching card (`<a class="card">` with kicker, title, description) to the grid in `index.html`.

All pages follow shared conventions:

- **Language/direction**: `<html lang="fa" dir="rtl">`; content is written in Persian. English kickers/labels inside RTL text use `direction:ltr; unicode-bidi:isolate`.
- **Milli brand palette**, defined as CSS variables in `:root` on every page: navy background `--bg:#16205C`, gold accent `--gold:#F2A81E` / `--gold-hi:#FFC24D`, plus derived surface/line/text tokens (`--surface`, `--line`, `--t-hi`, `--t-body`, `--t-mut`). New pages should copy this token block rather than invent colors.
- **Typography**: Vazirmatn from Google Fonts (the only external dependency), falling back to Tahoma.
- **Deck mechanics**: each deck implements its own slide navigation inline — `<section class="slide">` elements toggled via an `active` class, a top progress bar, prev/next controls with a Persian-digit counter, keyboard navigation (arrows, Home/End), and a print/reduced-motion fallback that shows all slides statically.
