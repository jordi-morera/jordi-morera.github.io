# Portfolio — Jordi Morera

Static portfolio built with **Astro + TypeScript + Tailwind CSS 4**. Each project has a card with a short pitch for recruiters and, below it, its README synced from GitHub.

## Getting started
```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # generates dist/
```

## How it works
- `src/data/site.ts` — your data (email, GitHub, LinkedIn…).
- `src/data/projects.ts` — **the single source of truth** for projects. Adding one = adding an object.
- `src/lib/readme.ts` — at build time, downloads `README.md` from `raw.githubusercontent.com`. If it fails (private repo, no network, not pushed yet), falls back to the copy in `src/readmes/<slug>.md`. Rewrites relative images and links so they point to the repo.
- `src/pages/projects/[slug].astro` — project card: pitch + highlights + stack + demo + README.

## Deployment
AWS S3 + CloudFront: `./deploy.sh <bucket> [distribution-id]`, or automatically via GitHub Actions (`.github/workflows/deploy.yml`).
