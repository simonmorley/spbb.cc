# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single static landing page for the **Scotts Park Bike Bus** — a parent-led group that cycles to Scotts Park Primary School (Bromley) every Friday. The site is one self-contained file, `public/index.html`, hosted on **Cloudflare Pages**.

## Architecture

Everything lives in `public/index.html`:
- All CSS is inline in a single `<style>` block in `<head>`. There is no build step, no external CSS/JS files, and no framework.
- The design system is driven by CSS custom properties in `:root` (`--ink`, `--paper`, `--sun`, `--grass`, `--accent`, etc.). Change colours there, not at call sites.
- Typography uses two Google Fonts loaded via `<link>`: **Fredoka** (headings, `.display`) and **DM Sans** (body).
- Page is a sequence of `<section>` blocks: hero → `#about` → `#when` → `#rules` → `#join` → footer. Inner content is constrained by `.wrap` (max ~1040px).
- The visual style is "neo-brutalist playful": thick `2.5px solid var(--ink)` borders with hard offset shadows (`box-shadow:0 6px 0 var(--ink)`). Reuse this pattern for new cards/buttons rather than inventing new shadows.
- Reveal animation: add classes `rise d1`–`d4` to fade/slide elements in on load. Respects `prefers-reduced-motion`.

## Repeated values to keep in sync

These are hardcoded in multiple places — update all occurrences together:
- **WhatsApp group link** (`https://chat.whatsapp.com/CZzQNvmk6lS2kNA5gCl3H4?mode=gi_t`) appears in the hero, about, join, and footer sections.
- **Meeting time** (Fridays, meet 8:15–8:20, depart 8:25) and the meeting point (Google Maps + what3words `unfair.chins.icons`) live in the `#when` section.

## Working on it

There is **no build step** — it's a plain static site. Preview by opening `public/index.html` directly, or run `npm run dev` (Cloudflare Pages dev server via Wrangler).

## Deployment

Hosted on Cloudflare Pages, project name `spbb-cc`, serving the `public/` directory (`pages_build_output_dir` in `wrangler.toml`). Two paths:
- **Git integration** (primary): pushes to `main` on GitHub auto-deploy. Build command is empty; output directory is `public`.
- **Direct upload**: `npm run deploy` → `wrangler pages deploy public`.

Do not add a framework or build tooling unless the site genuinely outgrows a single static file — the value here is that it's zero-dependency and instant to deploy.
