# AGENTS.md

## Cursor Cloud specific instructions

This repo is a single static marketing landing page (`index.html`) for "Veralogix
SecureConnect". There is no backend, build step, or framework — all styling/JS is
inline in `index.html` (Tailwind is loaded from a CDN). The only services are dev
tooling declared in `package.json`.

### Running the site (dev)

Serve the static page with the bundled `http-server`:

```
npx http-server -p 8080 -c-1
```

Then open `http://localhost:8080/`. `-c-1` disables caching, which is useful while
editing `index.html`. There is no hot reload — refresh the browser after edits.

### Notes / gotchas

- There is no real test suite: `npm test` is the npm placeholder and exits 1 by
  design. There is no lint or build command.
- `playwright` is listed as a dependency but is not used by any script in the repo;
  its browser binaries are not installed by `npm install`. Run
  `npx playwright install` only if you actually add Playwright-based tests.
- The `.github/workflows/jekyll-docker.yml` workflow is the default GitHub Jekyll
  template. The repo has no Jekyll config (`_config.yml`/`Gemfile`), so it does not
  reflect how this site is actually built or served — ignore it for local dev.
- A few feature cards in `index.html` overlap slightly on some viewport sizes; this
  is pre-existing content layout, not an environment problem.
