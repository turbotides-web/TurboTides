# AGENTS.md

## Purpose

This repository contains the Hugo source for the TurboTides marketing website at `https://www.turbotides.com/`. The site presents the TurboTides turbomachinery software product, engineering services, blog/news content, software case studies, testimonials, and a small "other software" area for related products such as FloTides, OpTides, and OASIS.

This file is written for AI agents working in the repo. Treat it as the operating manual for making changes safely and improving the codebase over time.

## High-Level Shape

- Static site generator: Hugo
- Theme: vendored `themes/tella` theme, heavily overridden from the project root
- Site config: `config.toml`
- Main content roots:
  - `content/_index.md`: homepage content assembled through shortcodes
  - `content/services/_index.md`: services page data in front matter
  - `content/blog/news/`: news articles
  - `content/blog/softwarecases/`: case studies
  - `content/other-software/`: other product and case-study landing pages
  - `content/contact/_index.md`: contact page content
  - `content/testimonials/_index.md`: testimonials landing page
- Custom templates and overrides: `layouts/`
- Site CSS assets: `assets/css/`
- Static files: `static/`
- Theme source retained in-tree: `themes/tella/`

## What Actually Drives the Site

The site is not a stock Tella install. The active behavior is mostly defined by root-level overrides:

- `layouts/_default/baseof.html` replaces the theme base layout and hardcodes Google Analytics.
- `layouts/partials/head.html`, `layouts/partials/header.html`, and `layouts/partials/footer.html` replace the theme partials.
- `layouts/index.html` adds homepage-specific body class behavior.
- Most branded page layouts live under `layouts/blog/`, `layouts/services/`, `layouts/software/`, `layouts/contact/`, `layouts/other-software/`, and `layouts/testimonials/`.
- The homepage is assembled through many custom shortcodes under `layouts/shortcodes/`.

In practice, root `layouts/` and `assets/` matter more than `themes/tella/` for day-to-day work.

## Tech Stack

### Hugo

- Hugo site configured in `config.toml`
- Theme configured as `tella`
- Goldmark unsafe rendering is enabled:
  - `[markup] goldmark = { renderer = { unsafe = true } }`
- Inline shortcodes are enabled
- `enableRobotsTXT = true`

### Hugo Version

Exact version is not pinned in this repo.

- CI workflow `.github/workflows/hugo.yml` installs Hugo Extended using `peaceiris/actions-hugo@v3` with:
  - `hugo-version: 'latest'`
  - `extended: true`
- Local `hugo` is not installed in this environment, so the exact version used by prior developers cannot be confirmed from the machine state.

Working assumption:

- The site requires Hugo Extended.
- CI currently builds against whatever the latest Hugo Extended release is at build time.
- This is a reproducibility risk and should be treated as unpinned infrastructure.

### Theme

- Base theme: `themes/tella`
- Theme is vendored directly into the repo, not currently checked out as a git submodule
- Original theme metadata:
  - `themes/tella/theme.toml`
  - upstream repo listed as `https://github.com/opera7133/tella`

### CSS / Styling

There are two parallel styling stories in the repo:

1. Theme-era Tailwind pipeline
- `themes/tella/assets/css/main.css` contains Tailwind directives
- `package.json` builds `themes/tella/assets/css/style.css`
- theme partials expect PostCSS/Tailwind processing of theme CSS

2. Active site-level pipeline
- Active head partial is `layouts/partials/head.html`
- It loads root `assets/css/style.css`, then concatenates root `assets/css/custom.css`, `home.css`, `news.css`, and `page-common.css` conditionally through Hugo Pipes
- Additional section CSS is separately loaded from root assets:
  - `software.css`
  - `services.css`
  - `testimonials.css`

Important inconsistency:

- `package.json` compiles Tailwind output into `themes/tella/assets/css/style.css`
- Active root `head.html` serves `assets/css/style.css`
- Root `assets/css/style.css` is already a compiled Tailwind stylesheet and appears to be the real production base
- That means the npm build target and the CSS actually bundled by the active templates are out of sync

Additional CSS observations:

- `assets/css/style.css` is compiled CSS, not source
- The file banner says Tailwind `v3.4.3`
- `package.json` and `package-lock.json` declare Tailwind 4 packages
- So the checked-in compiled CSS and current npm dependency set do not cleanly match

### JavaScript

There is no JS bundler or application framework. JavaScript is plain inline script blocks plus vendored third-party browser libraries under `static/js/`.

Patterns in use:

- Inline scripts inside templates and shortcodes
- Repeated `DOMContentLoaded` handlers across multiple files
- Manual DOM querying and event binding
- Animation and slider behavior implemented ad hoc in templates

Vendored third-party JS in `static/js/`:

- `swiper-bundle.min.js`
- `sweetalert2.min.js`
- `highlight.min.js`
- `highlightjs-line-numbers.min.js`
- `clipboard.min.js`

These are referenced directly in templates rather than managed through npm imports.

### Content/Data

- Front matter is a mix of TOML and markdown body content
- Structured data also lives in:
  - `data/testimonials.yaml`
  - `data/feature-grid1.json`
- Homepage content and several landing pages depend on shortcodes heavily

### Assets

- Static assets live under `static/`
- Images are organized by section: `static/img/home`, `static/img/news`, `static/img/products`, etc.
- A PDF exists at `static/docs/TurboTides.pdf`
- `static/CNAME` indicates custom domain hosting
- `static/.nojekyll` is present for GitHub Pages compatibility
- `.gitattributes` enables Git LFS for `*.mp4`

### Deployment / Hosting

Current checked-in deployment path:

- GitHub Actions workflow at `.github/workflows/hugo.yml`
- Deploys to GitHub Pages
- Uses `actions/upload-pages-artifact@v3` and `actions/deploy-pages@v4`
- Builds on push to `main`
- Uses Hugo Extended `latest`

Additional hosting clues:

- `static/CNAME` points to a custom domain flow for GitHub Pages
- `static/.nojekyll` is consistent with Pages static hosting

Conclusion:

- The active deploy setup is GitHub Pages, fronted by the custom domain `www.turbotides.com`

## Directory Guide

- `archetypes/`
  - Minimal Hugo archetype

- `assets/css/`
  - Active site CSS, including section-specific files
  - `style.css` is compiled base CSS, not a clean authoring source

- `content/`
  - Markdown content and section indexes
  - Heavy use of front matter-driven rendering and shortcodes

- `data/`
  - Small structured datasets used by shortcodes

- `layouts/`
  - Most important folder for active development
  - Overrides theme templates and defines custom page layouts and shortcodes

- `static/`
  - Raw files copied to final output unchanged
  - Images, JS libraries, icons, manifest, PDF, CNAME

- `themes/tella/`
  - Vendored upstream theme
  - Useful for reference, but many active templates are overridden by root files

- `cli-workspace/`
  - Scratch/output area for Codex and related agent work
  - Not part of the site source
  - Should stay out of production templates/content unless the user explicitly asks otherwise

## Content and Routing Conventions

### Main sections

Configured in `config.toml`:

- `showBlog = true`
- `mainSections = ['blog']`

But actual behavior is more custom than this suggests.

### News

- News index: `content/blog/news/_index.md`
- Uses:
  - `type = "blog"`
  - `layout = "news"`
  - `is_news_page = true`
- News article example:
  - `content/blog/news/news1/index.md`
  - uses `layout = "single-news"`

### Software cases

- Case studies live in `content/blog/softwarecases/`
- Index uses:
  - `type = "softwarecases"`
  - `is_news_page = true`
- Single items mostly rely on generic blog rendering unless otherwise specified

### Services

- Services page content is front-matter-driven
- `content/services/_index.md` contains an array of service cards under `services:`

### Other software

- Landing pages live in `content/other-software/...`
- Some pages attempt to inject standalone HTML via the `include-html` shortcode

## Working Conventions for Agents

### Where to look first

When changing behavior, inspect in this order:

1. `layouts/`
2. `assets/css/`
3. `content/`
4. `data/`
5. `static/`
6. `themes/tella/` only for fallback comparison or upstream reference

Do not assume the theme file is active just because it exists. Root-level overrides usually win.

### Preferred change style

- Favor cleanup while touching code
- Reduce duplication when it is safe to do so
- Normalize obvious inconsistencies instead of preserving them for nostalgia
- Keep Hugo templates simple and explicit
- Prefer moving repeated inline CSS/JS into shared assets when a change touches the same pattern in multiple places

### Agent scratch/output

- Use `cli-workspace/` for reports, notes, generated artifacts, and temporary outputs
- Do not scatter agent-generated files around the repo root
- Do not treat `cli-workspace/` as site content

### When editing content

- Preserve front matter format already used in the file
- Keep image paths rooted under `/img/...` unless there is a clear reason to change strategy
- Watch for section-specific flags such as `is_news_page`, `type`, and custom `layout`

### When editing templates

- Check whether the theme partial is overridden at root before changing theme files
- If a root override exists, prefer editing the root file
- Keep an eye on hardcoded URLs and nav items; the menu config in `config.toml` is not the sole source of truth

### When editing styles

- Assume `assets/css/style.css` is a generated base and avoid hand-editing it unless necessary
- Prefer changing the section-specific or custom CSS files in `assets/css/`
- If build pipeline work is needed, reconcile the root-vs-theme CSS path mismatch first instead of adding more layers

## Codebase Health Observations

### 1. Build pipeline is inconsistent

This is the biggest structural issue.

- Active templates load root `assets/css/style.css`
- npm scripts compile to `themes/tella/assets/css/style.css`
- Tailwind package versions indicate v4, while checked-in compiled CSS says v3.4.3
- CI workflow runs `hugo --minify` directly and does not run the npm build at all

Implication:

- The production CSS story is partially checked-in artifact, partially theme-era tooling, and not reliably reproducible from a clean machine

### 2. Hugo version is unpinned

- CI uses `latest` Hugo Extended
- No exact local version is documented

Implication:

- Future builds can drift or break without any repo change

### 3. Root templates duplicate and override theme behavior heavily

- Analytics appears in both theme and root base layouts
- Header, footer, and head are all custom at the root
- Navigation is manually hardcoded in `layouts/partials/header.html` even though `config.toml` also defines menus

Implication:

- Menu config is not the single source of truth
- Updating navigation requires template edits, not just config edits

### 4. Too much inline CSS and JS in templates

Examples:

- `layouts/partials/header.html`
- `layouts/contact/list.html`
- `layouts/software/list.html`
- multiple shortcodes under `layouts/shortcodes/`

Implication:

- Harder to reason about behavior
- Easy to duplicate bugs
- Hard to reuse or test

### 5. Encoding is messy

Several files show mojibake/garbled comments and text when read in this environment, especially comments that were likely authored in Chinese with inconsistent encoding handling.

Implication:

- Expect mixed encoding history
- Be careful when editing legacy files; normalize to UTF-8 where safe

### 6. "Other software" pages look fragile

- `include-html` shortcode uses `readFile` + `safeHTML`
- Content files reference paths like `other-software/optides/optides.html`
- The actual checked-in HTML files found here live under `layouts/other-software/cases/...`
- Those standalone HTML snippets include full `<!DOCTYPE html>`, `<html>`, `<head>`, and `<body>` documents, which is not normal Hugo partial content

Implication:

- This area likely has path drift and/or broken assumptions
- It also bypasses normal Hugo layout composition

### 7. Safety posture is loose in a few places

- Goldmark unsafe rendering is enabled globally
- `include-html` renders `readFile` output through `safeHTML`
- several template values are piped through `safeHTML` directly

Implication:

- Be cautious with externally sourced or user-provided content
- Avoid expanding this pattern unless there is a strong reason

### 8. Section/page conventions are custom and inconsistent

- News uses custom flags like `is_news_page`
- Software cases share blog-ish structure but not always the same templates
- Some pages rely on content front matter arrays, others on data files, others on hardcoded HTML in templates

Implication:

- Before changing a section, inspect one live example and its layout path rather than assuming a uniform Hugo model

### 9. Static library duplication exists between root and theme

- Some JS and manifest/favicon assets exist both under root `static/` and under `themes/tella/static/`

Implication:

- Root versions likely win, but there is extra noise and opportunity for confusion

## Standing Instructions for Future Agents

- Flag questionable code proactively. Do not silently work around structural problems if you see them.
- Default to cleaning things up on the spot when the cleanup is low-risk and local to the task.
- Do not preserve obvious duplication, dead paths, or mismatched conventions just because they are already in the repo.
- If a task touches navigation, CSS bundling, section templates, or "other software" pages, inspect adjacent files for duplication before editing.
- Prefer consolidating inline JS/CSS into reusable assets when doing medium or large changes.
- Prefer one clear source of truth over parallel config-plus-hardcode setups.
- If you discover build/deploy ambiguity, document the exact file paths and failure mode in your final response.

## Safe Defaults for Common Tasks

### Add or edit a news post

- Start from `content/blog/news/news1/index.md` as the structural reference
- Confirm `layout = "single-news"` and `is_news_page = true` if the new page should use the branded news template
- Place images under `static/img/news/`

### Add or edit a software case

- Use an existing file under `content/blog/softwarecases/` as the template
- Keep the summary explicit because list pages truncate from it
- Place cover images under `static/img/blog/`

### Change homepage content

- Inspect `content/_index.md`
- Then inspect the relevant shortcode in `layouts/shortcodes/`
- Then inspect the corresponding section CSS in `assets/css/home.css` or `assets/css/custom.css`

### Change global styling or layout shell

- Check `layouts/_default/baseof.html`
- Check `layouts/partials/head.html`
- Check `layouts/partials/header.html`
- Check `layouts/partials/footer.html`
- Confirm whether the change belongs in root assets instead of theme assets

## Recommended Follow-Up Cleanup Projects

These are good candidates if the repo is being stabilized:

1. Pin Hugo Extended to a known working version in CI and document it.
2. Reconcile the CSS pipeline so there is one real source of truth for Tailwind/base CSS.
3. Move repeated inline scripts into shared JS assets.
4. Normalize file encodings to UTF-8.
5. Replace `include-html` full-document snippets with proper Hugo layouts/partials.
6. Consolidate navigation so `config.toml` and header markup do not drift.

## Verification Notes

This repo was inspected locally, but `hugo` is not installed in the current environment, so a live site build was not executed during creation of this file. Any future agent changing build/deploy behavior should validate with an actual Hugo build before concluding the pipeline is fixed.
