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

### Adding a new section folder to the CMS

Sveltia CMS does not natively support nested folders, so each folder under `content/` that contains an `_index.md` needs its own collection entry in `static/admin/config.yml`. When a new section folder is added to the site, register it as follows:

1. Add a collection entry to `static/admin/config.yml`. Copy an existing nested-folder collection (e.g. `assembly-pages`) as a template — the field definitions are shared via the `*page_fields` and `*index_file_fields` YAML anchors, so only `name`, `label`, `label_singular`, and `folder` need to change:

   ```yaml
   - name: my-section-pages
     label: My Section Pages
     label_singular: My Section Page
     folder: content/my-section
     create: true
     extension: md
     format: yaml-frontmatter
     slug: "{{slug}}"
     fields: *page_fields
     index_file:
       fields: *index_file_fields
   ```

2. Order collection entries to match the `weight:` value in each section's `_index.md` (lowest first, at each nesting level). This keeps the CMS sidebar order aligned with the site navigation.
3. If a `label` or `label_singular` contains `: ` (colon-space), wrap it in double quotes — plain YAML scalars cannot contain `: `. For example: `label: "Lottery: Selection Pages"`.
4. Run `uvx yamllint static/admin/config.yml` before committing.

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
