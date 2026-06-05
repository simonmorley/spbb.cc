# spbb.cc — Scotts Park Bike Bus

A single static landing page for the **Scotts Park Bike Bus**, a parent-led group that cycles to Scotts Park Primary School (Bromley) together every Friday.

The whole site is one self-contained file — `public/index.html` — with all CSS inline and no build step. It is hosted on **Cloudflare Pages**.

## Develop

Preview locally with the Cloudflare Pages dev server:

```bash
npm install
npm run dev
```

Or just open `public/index.html` in a browser.

## Deploy

Two options:

### 1. Git integration (recommended)

Cloudflare Pages is connected to this GitHub repo and redeploys automatically on every push to `main`.

- **Build command:** _(none)_
- **Build output directory:** `public`

### 2. Direct upload via Wrangler

```bash
npm run deploy
```

This runs `wrangler pages deploy public --project-name spbb-cc`. The first run will prompt you to authenticate (`wrangler login`) and create the Pages project if it doesn't exist yet.
