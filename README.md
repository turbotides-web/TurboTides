# TurboTides Website

This repository contains the Hugo source for the TurboTides marketing site.

## Current Deployment Path

- Hosting/deploy target: GitHub Pages
- Production deploy trigger: push to `main`
- Deploy workflow: [`.github/workflows/hugo.yml`](.github/workflows/hugo.yml)
- Custom domain is configured via [`static/CNAME`](static/CNAME)

Important:

- Changes in this repo do not go live until they are committed and pushed to the connected GitHub repository.
- Once a commit reaches `main`, GitHub Actions is expected to build and deploy the site automatically.

## Verified Hugo Baseline

This repo currently builds successfully with:

- Hugo Extended `0.160.1`

The GitHub Pages workflow is pinned to that version.

## Local Development

### Preview locally

```powershell
hugo server
```

This starts the local Hugo dev server, typically at `http://localhost:1313/`.

### Production-style build

```powershell
hugo --minify
```

This writes the generated site to `public/`.

## Current Build Reality

Right now, the verified site build path is Hugo itself:

- Local verified build command: `hugo --minify`
- CI build command: `hugo --minify`

This is intentional documentation of the repo's current working state, not a statement that the build pipeline is fully cleaned up.

## About `package.json`

The repo still contains inherited npm/Tailwind scripts from the Tella theme, but the root npm entry points now map to the verified Hugo workflow:

- `npm run start`
- `npm run build`

Legacy theme-era commands are still available as:

- `npm run legacy:start`
- `npm run legacy:build`

Those legacy scripts still target `themes/tella/assets/css/...`, while the active root templates load CSS from `assets/css/...`.

That means:

- the legacy npm/Tailwind path is not yet the trusted source of truth for production output
- future cleanup should reconcile the CSS pipeline before relying on the npm scripts as canonical

Until that cleanup is done, prefer `npm run start`, `npm run build`, or the equivalent Hugo commands above for normal site generation and verification.

## Maintenance Notes

- Main site configuration lives in [`config.toml`](config.toml)
- Active templates mostly live in [`layouts/`](layouts)
- Active CSS mostly lives in [`assets/css/`](assets/css)
- Static assets live in [`static/`](static)
- A more detailed AI-oriented maintenance guide lives in [`AGENTS.md`](AGENTS.md)

## Recommended Workflow

For maintenance work on this repo:

1. Make one small scoped change.
2. Run local Hugo verification.
3. Manually verify the affected pages.
4. Commit the approved change.
5. Push only when you are ready for that change to deploy from `main`.
