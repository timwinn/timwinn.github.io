# Quarto Blog — Project Conventions

## Overview
Quarto blog at https://timwinn.github.io. Computational skills for healthcare professionals.

## Directory Structure
```
timwinn.github.io/
├── _quarto.yml           # Site configuration
├── index.qmd             # Home page (blog listing)
├── about.qmd             # About page
├── styles.css            # Custom styles
├── posts/                # All blog posts
│   ├── _metadata.yml     # Post defaults (freeze: true)
│   └── YYYY-MM-DD-slug/  # Individual post directories
│       └── index.qmd
├── _freeze/              # Frozen computational outputs (MUST commit)
├── _site/                # Build output (gitignored)
└── .github/workflows/
    └── publish.yml       # Auto-deploy on push to main
```

## Blog Posts

### Location
`posts/YYYY-MM-DD-slug/index.qmd` — one directory per post, kebab-case slugs.

### Frontmatter Template
```yaml
---
title: "Post Title"
description: "Brief description for SEO and listings"
author: "Timothy Winn, MD"
date: "YYYY-MM-DD"
categories: [category1, category2]
image: "image.jpg"   # optional thumbnail
draft: false          # true to hide from listings
---
```

### Categories
`tools` · `mathematics` · `programming` · `data-science` · `medical-education` · `reflections`

## Freeze Strategy
- `freeze: true` is set in `posts/_metadata.yml`
- Run code **locally** — frozen outputs go to `_freeze/`
- GitHub Actions only renders markdown → HTML (no code execution in CI)
- Always commit `_freeze/` changes after rendering posts with code

## Commands
```bash
quarto preview          # Local dev server with live reload
quarto render           # Render entire site
quarto render posts/YYYY-MM-DD-slug/index.qmd  # Render single post
```

## Publishing
Push to `main` → GitHub Actions renders and deploys to `gh-pages` automatically.

Manual: `quarto publish gh-pages`

## Commit Messages
Conventional commits: `feat:`, `fix:`, `docs:`, `style:`, `refactor:`

Examples:
- `feat: add post on Python data visualization`
- `fix: correct broken link in about page`
- `docs: update CLAUDE.md conventions`

## Assets
Store images/data in the post directory. Reference with relative paths: `![Caption](image.png)`
