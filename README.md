# vbtronic.com

Personal website of Viktor Brunclík. Built with [Hugo](https://gohugo.io/).

## Prerequisites

- [Hugo](https://gohugo.io/installation/) (extended edition, v0.145.0+)

## Local Development

```bash
# Start the development server with live reload
hugo server -D

# Build the site (output goes to ./public/)
hugo
```

The dev server runs at `http://localhost:1313` by default.

## Content

All content lives in the `content/` directory as Markdown files:

- `content/_index.md` — Home page (bio, projects)
- `content/posts/` — Blog posts

### Adding a New Post

Create a new Markdown file in `content/posts/`:

```bash
hugo new posts/my-new-post.md
```

Or manually create a file with frontmatter:

```markdown
---
title: "My New Post"
date: 2026-02-07
description: "A brief description."
---

Your content here.
```

## Deployment (CI/CD)

This site is deployed automatically to GitHub Pages via GitHub Actions.

### Setup

1. Go to your repository on GitHub: **Settings → Pages**
2. Under **Source**, select **GitHub Actions**
3. Push to the `main` branch — the site will build and deploy automatically

> **Important:** Pages must be enabled (steps 1–2) *before* the first push, otherwise the workflow will fail with a `configure-pages` error.

The workflow is defined in `.github/workflows/deploy.yml`.

### Custom Domain

The primary domain is `www.vbtronic.com`, with the apex `vbtronic.com` redirecting to it.

1. In **Settings → Pages**, enter `www.vbtronic.com` as your custom domain
2. Add DNS records with your domain registrar:
   - `www` subdomain: **CNAME** record pointing to `vbtronic.github.io`
   - Apex domain (`vbtronic.com`): **A** records pointing to GitHub Pages IPs (this enables the redirect to `www`):
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
3. Check **Enforce HTTPS** in Settings → Pages once the certificate is provisioned
4. Wait for DNS propagation (can take up to 24h)

## Project Structure

```
├── content/          # Markdown content
│   ├── _index.md     # Home page
│   └── posts/        # Blog posts
├── layouts/          # HTML templates
│   ├── _default/     # Default templates
│   └── index.html    # Home page template
├── static/           # Static assets (CSS, images)
│   └── css/
├── hugo.toml         # Hugo configuration
└── .github/
    └── workflows/    # CI/CD
```

## License

Source code is licensed under the [MIT License](LICENSE).

Content (articles, blog posts, text) © Viktor Brunclík. All rights reserved.
