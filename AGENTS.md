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

Green on white — this is the site's own identity, not bruncsoft.com's. Do not restyle it
to match bruncsoft.com; only the *content* facts about the studio are kept in step.

- **Light is the default.** Dark only when the visitor picks it or their system explicitly
  asks for dark. `:root` holds the dark palette, `[data-theme="light"]` overrides it, and
  the pre-paint script in `baseof.html` always sets `data-theme` before first paint
- Accent: `#16a34a` light / `#22c55e` dark
- Background: `#f5f6f8` light (elevated `#ffffff`) / `#121418` dark (elevated `#1a1d23`)
- Text headings: `#1a1a2e` / `#f0f0f2`
- Font body: Inter. Font mono: JetBrains Mono, for dates and code only
- Radii: 12px cards, 8px small elements, 20px pills
- Nav: hamburger opens a dropdown panel anchored under the header — it is
  `position: absolute` inside `<header>`, so it must stay inside it
- Every colour goes through a `--color-*` custom property. Never hard-code a hex outside
  the two palette blocks at the top of `style.css`

## Deployment

Pushing to `main` triggers automatic deployment via GitHub Actions (`.github/workflows/deploy.yml`).
