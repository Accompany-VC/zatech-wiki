# ZATech Wiki

This is the source for the ZATech community wiki built with Hugo + Docsy.

## Quickstart (local)

Requirements:
- Hugo Extended (>= 0.150)
- Go (for Hugo Modules)
- Node.js 18+ (for PostCSS used by Docsy)

Steps:
```bash
# 1) Clone
git clone https://github.com/zatech/zatech-wiki.git
cd zatech-wiki

# 2) Install Hugo modules (Docsy, Font Awesome)
hugo mod tidy

# 3) Install PostCSS toolchain
npm install

# 4) Run the dev server
npm run dev
```

The site will be available at `http://localhost:1313/`.

## Project structure

- `content/`
  - `faqs/` — Frequently Asked Questions
  - `channels/` — channel-specific pages
  - `pages/` — general pages (e.g. commercial channels)
  - `blog/` — longer-form guides and posts
- `assets/scss/` — custom styles; `_variables_project.scss` and `_styles_project.scss`
- `static/` — static files (images, favicons, etc.)
- `layouts/` — Docsy overrides (e.g. `partials/footer.html`)
- `hugo.toml` — site config

## Contributing

We welcome issues and PRs from the community.

- Create a new branch for your change.
- For small content edits, go straight to a PR.
- For structural or design changes, please open an issue to discuss.

Content conventions:
- Prefer Markdown, keep front matter minimal: `title`, optional `summary`.
- Use relative links within the site (e.g. `/faqs/howtoinvite/`).
- Images go under `static/images/...` and use absolute paths like `/images/...` in Markdown.

Writing style:
- Be clear and concise.
- South African audience and context.
- Avoid personal info or private channel content unless explicitly allowed.

## Blog posts

Longer, living documents belong in `content/blog/`. Use this front matter:
```toml
+++
title = "Post title"
date = 2025-01-01T00:00:00Z
summary = "Short summary shown on the blog list"
author = "Your Name"
+++
```

## Navigation

Top navbar items are defined in `hugo.toml` under `[menu.main]`.

## Deployment

GitHub Actions are set up to:
- Build and deploy to GitHub Pages on pushes to `main`: `.github/workflows/pages.yml`.
- Provide PR deploy previews: `.github/workflows/pr-preview.yml`.

To enable Pages in the repo:
- Settings → Pages → Build and deployment → Source: GitHub Actions.

## License

Content is © respective authors. Code and configuration is MIT unless otherwise noted.
