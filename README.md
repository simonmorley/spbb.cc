# spbb.cc — Scotts Park Bike Bus

A single static landing page for the **Scotts Park Bike Bus**, a parent-led group that cycles to Scotts Park Primary School (Bromley) together every Friday.

The whole site is one self-contained file — `public/index.html` — with all CSS inline and no build step. It is hosted on **Cloudflare Workers Static Assets** (the `public/` directory is served directly; no Worker script).

## Develop

Preview locally with the Cloudflare Pages dev server:

```bash
npm install
npm run dev
```

Or just open `public/index.html` in a browser.

## Deploy

Two options:

### 1. Git integration (active)

Cloudflare is connected to this GitHub repo and redeploys on every push to `main`,
running `npx wrangler deploy` against `wrangler.toml`.

### 2. Direct upload via Wrangler

```bash
npm run deploy        # wrangler deploy
```

The first local run prompts you to authenticate (`npx wrangler login`).
