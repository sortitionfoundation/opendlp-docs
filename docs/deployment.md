# ABOUTME: Deployment guide for the OpenDLP documentation site

# ABOUTME: Covers static site deployment, CMS authentication setup, and content editing workflow

# Deploying the OpenDLP Documentation Site

This guide covers deploying the Hugo documentation site and setting up
Sveltia CMS for browser-based content editing.

## Prerequisites

- A GitHub account with access to the `sortitionfoundation/opendlp-docs` repository
- Hugo installed locally (v0.100.0 or later) if you want to preview before pushing

## Deployment via GitHub Pages

The site is automatically built and deployed to GitHub Pages whenever changes
are pushed to the `main` branch. The workflow is defined in
`.github/workflows/deploy.yml`.

### How it works

1. A push to `main` triggers the deploy workflow
2. The workflow builds the site with `hugo --minify`, setting the base URL
   automatically based on the GitHub Pages configuration
3. The built site is uploaded as a GitHub Pages artifact and deployed

The workflow can also be triggered manually from the **Actions** tab in GitHub
(via `workflow_dispatch`).

### Initial setup

To enable GitHub Pages deployment for the repository:

1. Go to the repository **Settings > Pages**
2. Under **Source**, select **GitHub Actions**
3. Push a change to `main` (or manually trigger the workflow from the Actions tab)

### Custom domain

To serve the site from a custom domain instead of `<org>.github.io/<repo>`:

1. In **Settings > Pages**, enter your custom domain
2. Configure DNS as described in
   [GitHub's custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

The deploy workflow automatically picks up the correct base URL — no changes
to `hugo.toml` are needed.

## Building locally

To preview the site locally:

```bash
just serve    # Dev server on localhost:1313 (with drafts)
just build    # Build to public/
```

## Content editing with Sveltia CMS

Sveltia CMS provides a browser-based editor at `/admin/` on the deployed site.
Editors can create and update pages through a visual interface — changes are
committed directly to the GitHub repository.

After content is edited via the CMS, changes are committed to GitHub and
the site is automatically rebuilt and deployed via GitHub Actions.

### Local editing (no auth needed)

When running the site locally with `just serve`, visit `http://localhost:1313/admin/`
and click "Work with Local Repository". The browser will prompt you to select the
root directory of the `opendlp-docs` repo. Changes are written directly to your local
files — no GitHub auth required. This is useful for drafting content before pushing.

### Quick start: token-based sign-in

The simplest way to use the CMS requires no additional infrastructure:

1. Deploy the site (the `/admin/` path is included in the static output)
2. Visit `https://your-docs-domain/admin/`
3. Click "Sign in with GitHub" then choose "Sign in with token"
4. Generate a GitHub personal access token at https://github.com/settings/tokens
   with the `repo` scope
5. Paste the token into the prompt

This works immediately with no OAuth setup. It's suitable for a small number
of editors who each have GitHub accounts.

### Full setup: OAuth sign-in for teams

For a smoother sign-in experience (no token management), set up OAuth
authentication using the Sveltia CMS Authenticator on Cloudflare Workers.

#### Step 1: Deploy the OAuth authenticator

The authenticator is a small Cloudflare Workers script that handles the
OAuth flow between the browser and GitHub.

1. Go to https://github.com/sveltia/sveltia-cms-auth
2. Click the "Deploy to Cloudflare Workers" button, or clone and run
   `wrangler deploy` locally
3. Note your worker URL: `https://sveltia-cms-auth.<SUBDOMAIN>.workers.dev`

Cloudflare Workers has a generous free tier — this will cost nothing for
typical documentation editing usage.

#### Step 2: Register a GitHub OAuth App

1. Go to https://github.com/organizations/sortitionfoundation/settings/applications/new
   (or your GitHub org's settings)
2. Fill in:
   - **Application name:** `OpenDLP Docs CMS` (or similar)
   - **Homepage URL:** Your docs site URL
   - **Authorization callback URL:** `https://sveltia-cms-auth.<SUBDOMAIN>.workers.dev/callback`
3. Click "Register application"
4. On the next page, click "Generate a new client secret"
5. Save both the **Client ID** and **Client Secret**

#### Step 3: Configure the Cloudflare Worker

In the Cloudflare dashboard, go to your worker's Settings > Variables and add:

| Variable               | Value                          | Encrypt? |
| ---------------------- | ------------------------------ | -------- |
| `GITHUB_CLIENT_ID`     | Your OAuth app's Client ID     | No       |
| `GITHUB_CLIENT_SECRET` | Your OAuth app's Client Secret | Yes      |

Optionally set `ALLOWED_DOMAINS` to restrict which domains can use the
authenticator (e.g. `your-docs-domain.org`).

#### Step 4: Update CMS configuration

In `docs-site/static/admin/config.yml`, uncomment and update the `base_url`:

```yaml
backend:
  name: github
  repo: sortitionfoundation/opendlp-docs
  branch: main
  base_url: https://sveltia-cms-auth.<SUBDOMAIN>.workers.dev
```

Rebuild and redeploy the site.

#### Step 5: Test

1. Visit `https://your-docs-domain/admin/`
2. Click "Sign in with GitHub"
3. You should be redirected to GitHub for authorization
4. After authorizing, you'll be returned to the CMS editor

### Access control

Editors need:

- A GitHub account
- Write access to the `sortitionfoundation/opendlp-docs` repository

The CMS commits changes using the editor's GitHub identity, so all edits
are attributed to the person who made them.

## Content workflow

1. Editor signs in at `/admin/` and makes changes (or pushes Markdown changes via git)
2. Changes are committed to the `main` branch on GitHub
3. GitHub Actions automatically builds and deploys the updated site to GitHub Pages
