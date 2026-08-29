# AGENTS.md

Instructions for AI coding agents working on this repository.

## Project Overview

This is a Hugo static site for vbtronic.com — Viktor Brunclík's personal website.

## Tech Stack

- **Static site generator**: Hugo (extended edition)
- **Hosting**: GitHub Pages
- **CI/CD**: GitHub Actions
- **Styling**: Custom CSS (no frameworks)
- **Fonts**: Inter (body), JetBrains Mono (code/accents)

## Commands

```bash
# Local dev server with drafts
hugo server -D

# Build for production
hugo --minify

# Create a new post
hugo new posts/my-post-title.md
```

## Content Authoring

- All content is in `content/` as Markdown files with YAML frontmatter
- Posts go in `content/posts/` with frontmatter: `title`, `date`, `description`
- Home page content is in `content/_index.md`
- Images should be placed in `static/images/`
- **Date/time in frontmatter must use the actual current time** — never hardcode `12:00:00` or guess. Use `date` command to get the real time before creating content

## Code Conventions

- **CSS**: No frameworks. All styles in `static/css/style.css`. Use CSS custom properties for theming
- **Templates**: Hugo Go templates in `layouts/`. Base template is `layouts/_default/baseof.html`
- **No JavaScript** unless absolutely necessary. Keep it static and fast
- **No build tools** beyond Hugo itself

## Design System

Shared with bruncsoft.com — keep the two sites in step.

- **Light is the default.** Dark only when the visitor picks it or their system asks for it
- Background: `#ffffff` light / `#141414` dark; card and footer surface `#f5f5f7` / `#1e1e1e`
- Accent: `#0071e3` light / `#2997ff` dark (Apple blue)
- Text: `#1d1d1f` / `#f5f5f7` (primary), `#6e6e73` / `#a1a1a6` (secondary)
- Font body: Inter. Font mono: JetBrains Mono, for dates and code only
- Radii: `--radius` 20px (cards), `--radius-sm` 14px (inputs, small cards), `--radius-xs` 8px, `--radius-pill` for buttons
- Container max-width: 1080px (`.container--narrow` is 700px for prose)
- Nav: 56px translucent bar, hamburger opens a full-screen menu overlay at every width
- Every colour goes through a `--color-*` custom property; the short `--bg` / `--accent` /
  `--radius` aliases in `:root` are the bruncsoft token names, so markup copied from
  bruncsoft.com works without edits

## Deployment

Pushing to `main` triggers automatic deployment via GitHub Actions (`.github/workflows/deploy.yml`).
