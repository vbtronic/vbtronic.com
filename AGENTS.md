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

## Code Conventions

- **CSS**: No frameworks. All styles in `static/css/style.css`. Use CSS custom properties for theming
- **Templates**: Hugo Go templates in `layouts/`. Base template is `layouts/_default/baseof.html`
- **No JavaScript** unless absolutely necessary. Keep it static and fast
- **No build tools** beyond Hugo itself

## Design System

- Background: `#0a0a0a`
- Accent: `#00b4d8` (electric cyan)
- Text: `#e0e0e0` (body), `#f5f5f5` (headings)
- Font body: Inter
- Font mono: JetBrains Mono
- Container max-width: 800px
- Dark theme only

## Deployment

Pushing to `main` triggers automatic deployment via GitHub Actions (`.github/workflows/deploy.yml`).
