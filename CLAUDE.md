# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Personal portfolio and blog site for Scott Grant, Product Marketing Manager. Built with Astro v6, deployed on Netlify via GitHub.

- **Live site:** deployed on Netlify (connected to github.com/scottie-g/portfolio)
- **Local dev:** `npm run dev` → http://localhost:4321

## Commands

```bash
npm run dev      # Start local dev server
npm run build    # Build for production (output to dist/)
npm run preview  # Preview the production build locally
```

## Architecture

Static site — no database, no backend, no auth. Everything is files.

### Adding a blog post

Create a new `.md` file in `src/content/blog/`. Required frontmatter:

```markdown
---
title: "Post title"
date: 2026-05-14
description: "One sentence summary shown in the post list."
---

Post content here...
```

The filename becomes the URL slug (e.g. `my-post.md` → `/blog/my-post`).

### Pages

- `src/pages/index.astro` — Homepage
- `src/pages/portfolio.astro` — Work/case studies
- `src/pages/blog/index.astro` — Blog listing (auto-populated from content collection)
- `src/pages/blog/[slug].astro` — Individual blog post template
- `src/pages/contact.astro` — Contact page

### Layout

`src/layouts/Layout.astro` contains the shared layout: global styles, nav, and footer. All pages use this layout.

### Content collection

Blog posts are managed via Astro's Content Layer API. Config is in `src/content.config.ts`. Posts live in `src/content/blog/`.

## Deploying changes

Push to `master` on GitHub — Netlify auto-deploys on every push.

```bash
git add -A
git commit -m "describe what you changed"
git push
```
