# OpenDLP Docs

## Project Overview

This is the documentation site for **OpenDLP** (Open Democratic Lottery Platform), an open-source tool for running Citizens' Assemblies and democratic lotteries, built by the [Sortition Foundation](https://www.sortitionfoundation.org).

The site is built with [Hugo](https://gohugo.io/) and uses a custom theme styled after the [GOV.UK Design System](https://design-system.service.gov.uk/) with Sortition Foundation branding.

## OpenDLP Docs

The site is live at <https://docs.gh.sortitionlab.org>

The source code can be found at <https://github.com/sortitionfoundation/opendlp-docs>

Whenever you edit the site there are GitHub Actions that will rebuild the site and publish it.

## Editing for most people

### Quick version

Go to `/admin/` on the live site - [direct link](https://docs.gh.sortitionlab.org/admin/) click the "sign in with github" link. Once you've done that, you can edit in the browser and click "save". Around 30 seconds later your edit will be live on the site.

### Longer version

Prerequisites:

- You need an account on https://github.com/ - if you don't have one, [create an account here](https://github.com/signup).
- One of the technical team needs to allow you to edit this git repo. For the technical team, you can [manage access here](https://github.com/sortitionfoundation/opendlp-docs/settings/access).

Editing

- Go to `/admin/` on the live site - [direct link](https://docs.gh.sortitionlab.org/admin/) click the "sign in with github" link.
- Edit in the browser and click "save".
- Around 30 seconds later your edit will be live on the site.

What happens when you edit? You don't need to know this but for interest:

- The admin page running in your browser adds a git commit to the github repo.
- That triggers a process that rebuilds the site with your edits and then copies it to the live site.
- You can then reload the updated site in your browser.

## Editing and Developing locally

You need to [install hugo](https://gohugo.io/installation/) and [install just](https://github.com/casey/just?tab=readme-ov-file#installation).

Then you can build the site with `just build` and you can open `public/index.html` in your web browser.

If you want live updates in your web browser while you edit and save the local files, you can run `just serve` and then open <http://localhost:1313/> in your web browser.

## Deployment

Live deployment is a little complicated - we have [full deployment docs](docs/deployment.md) in this repo.
