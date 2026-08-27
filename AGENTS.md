# AGENTS.md

Guidance for AI coding agents (Cursor Cloud Agents and others) working in this repository.

## What this project is

**Nepantla Garden** — a public digital garden built with [Quartz](https://quartz.jzhao.xyz)
that publishes selected **teaching materials and writing** from a personal Obsidian vault.

- Notes live as Markdown in `content/`.
- The private Obsidian vault is **separate** (synced via Obsidian Sync) and is **not**
  in this repo. Only finished notes are copied here to be published.
- The site deploys automatically to GitHub Pages on every push to `main`.

## Running / previewing

The Cloud Agent environment (`.cursor/environment.json`) installs dependencies and
starts a live-preview server automatically:

- Install: `npm ci`
- Preview server: `npx quartz build --serve --port 8080`
- URL: http://localhost:8080/

To run it manually: `npm ci` then `npx quartz build --serve`.

## What gets published (opt-in)

Publishing is **opt-in** via the `explicit-publish` plugin. A note is published **only**
if its frontmatter contains:

```yaml
---
title: My note
publish: true
---
```

Notes without `publish: true` are excluded from the site (URL 404s and they don't appear
in navigation, search, or the graph). The `private/` folder is also git-ignored, so
anything there never reaches GitHub. This means the default is **private** — nothing is
published unless explicitly flagged.

## How content gets here

Content flows one way, vault → repo:

1. In Obsidian, mark a finished note with `publish: true`.
2. Copy that note's Markdown into `content/` in this repo (preserve any folder like
   `teaching/` or `writing/`). In Cursor you can ask the agent to do this copy + commit.
3. Commit and push to `main`; the GitHub Pages workflow builds and deploys.

Never bolt Git or another sync tool onto the live vault — keep that on Obsidian Sync only.

## Conventions

- Keep all publishable notes under `content/`. Use Obsidian-style `[[wikilinks]]`.
- Do not commit `node_modules/` or `public/` (both are git-ignored).
- Prefer configuration changes in `quartz.config.default.yaml` (title, colors, plugins).
- The site's `baseUrl` in `quartz.config.default.yaml` must match where it's hosted
  (currently `cgmsf.github.io/fall2024`); update it if the repo is renamed or a custom
  domain is added. It currently assumes the repo is named `nepantla-garden`
  (`cgmsf.github.io/nepantla-garden`).

## Testing changes

- After content or config changes, run `npx quartz build --serve` and load the site in a
  browser. Verify: the changed page renders, `[[wikilinks]]` resolve, and any note that
  should be private is absent (returns 404).
- When demonstrating a change, include a screenshot or short recording of the site.
