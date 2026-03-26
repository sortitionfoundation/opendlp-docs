# AGENTS.md

## Project Overview

This is the documentation site for **OpenDLP** (Open Democratic Lottery Platform), an open-source tool for running Citizens' Assemblies and democratic lotteries, built by the Sortition Foundation.

The site is built with [Hugo](https://gohugo.io/) and uses a custom theme styled after the GOV.UK Design System with Sortition Foundation branding.

## Key Directories and Files

- `hugo.toml` — Site configuration, menu structure, and site-wide parameters
- `content/` — All documentation pages as Markdown with YAML/TOML frontmatter
- `themes/govuk-sortition/` — Custom Hugo theme (layouts, partials, CSS). Committed directly, not a submodule
- `static/files/` — Downloadable assets (e.g. example CSV files)
- `static/admin/` — Sveltia CMS configuration for browser-based editing
- `justfile` — Task runner: `just build`, `just serve`, `just clean`
- `docs/deployment.md` — Documents the current deployment process and how non-technical users edit the site via Sveltia CMS. Read this for deployment context

## Content Editing

Content lives in `content/` as Markdown files. When editing or creating content, work directly with the Markdown files — do not use the CMS.

Non-technical contributors may edit via the Sveltia CMS at `/admin/`, which commits changes to GitHub. See `docs/deployment.md` for details on that workflow.

The menu is defined in `hugo.toml` under `[menu]`. New pages need a corresponding menu entry there to appear in the navigation.

## Theme

The theme at `themes/govuk-sortition/` is lightweight and custom-built:

- Uses GOV.UK Frontend CSS/JS from CDN (v5.11.1)
- Custom CSS in `static/css/style.css` with Sortition Foundation brand colours
- Layouts: `baseof.html` (shell), `single.html` (content pages), `list.html` (sections), `index.html` (home with hero + feature cards)
- Partials: `header.html` and `footer.html`
- No custom shortcodes

## Building and Running

Requires Hugo extended (currently v0.123.7):

```bash
just serve    # Dev server on localhost:1313 (with drafts)
just build    # Build to public/
just clean    # Remove public/
```

## CI/CD

GitHub Actions runs `hugo --minify` on all branches and PRs to catch build errors (`.github/workflows/build.yml`).

The deployment process is currently in transition from manual rsync-based deployment towards GitHub Actions. See `docs/deployment.md` for the current state.

## Conventions

- All code files must start with a two-line comment explaining what the file does, each line prefixed with `ABOUTME: `
- Hugo config uses TOML format
- Content frontmatter can be TOML or YAML (the archetype uses TOML)
- The site renders unsafe HTML in Markdown (configured in `hugo.toml` under `[markup.goldmark.renderer]`)
