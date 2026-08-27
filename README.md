# Nepantla Garden

A public digital garden — teaching materials and writing from the borderlands — built
with [Quartz](https://quartz.jzhao.xyz) and published to GitHub Pages.

Notes are drafted privately in Obsidian; only notes marked `publish: true` are copied
into `content/` and published here.

## Preview locally

```bash
npm ci
npx quartz build --serve
```

Then open http://localhost:8080/.

## Publish a note

1. In Obsidian, add `publish: true` to the note's frontmatter.
2. Copy the note into `content/` (keep its folder, e.g. `teaching/` or `writing/`).
3. Commit and push to `main` — GitHub Pages builds and deploys automatically.

Anything without `publish: true`, and anything in `private/`, stays out of the site.

## Configuration

Site title, colors, and plugins live in `quartz.config.default.yaml`. Update `baseUrl`
there if the site moves to a different URL or custom domain.

---

Built with Quartz (MIT). See `LICENSE.txt`.
