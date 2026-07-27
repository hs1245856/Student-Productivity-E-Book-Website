# Productivity for University Students — Website

A React + Vite + Tailwind CSS site for the eBook *Productivity for University Students* by Haseeb Ur Rehman.

## Getting started

```bash
npm install
npm run dev
```

Open http://localhost:5173

## Build for production

```bash
npm run build
npm run preview   # preview the production build locally
```

## Deploy on Vercel

1. Push this folder to a GitHub repo.
2. Import the repo in Vercel — the included `vercel.json` and Vite's own
   detection mean no manual configuration is required.
3. Build command: `npm run build` · Output directory: `dist` (already set).

## Project structure

```
├── index.html            # document shell + SEO/OG/Twitter/Schema.org tags
├── public/
│   └── favicon.svg
├── src/
│   ├── main.jsx           # React entry point
│   ├── App.jsx            # the entire site (single component, see below)
│   └── index.css          # Tailwind directives
├── tailwind.config.js
├── postcss.config.js
├── vite.config.js
└── vercel.json
```

## Notes

- `App.jsx` is intentionally a single large component (as it was originally
  built as a self-contained artifact). It works as-is with Vite/React —
  nothing further to wire up — but if you'd like it split into
  `components/Nav.jsx`, `components/Hero.jsx`, etc. for easier maintenance,
  that's a straightforward follow-up refactor.
- Worksheet/cheat-sheet thumbnails and the free-sample PDF are embedded as
  base64 data URIs directly in `App.jsx` so the project has zero external
  asset dependencies. For a real production deployment you'll likely want
  to move these into `public/` or a CDN/object-storage bucket and swap the
  data URIs for `<img src="/worksheets/...">` — this keeps the repo lean
  and lets browsers cache images separately from your JS bundle.
- Update `og-cover.jpg` (referenced in `index.html`) by adding a real cover
  image to `public/`.
- Fonts (Playfair Display, Inter, Manrope) load via `@import` inside
  `App.jsx`'s own `<style>` block. For faster first paint in production,
  consider moving that `@import` into `index.html`'s `<head>` as a
  `<link rel="preconnect">` + stylesheet `<link>` instead.
