# Portfolio site

Static site. No build step, no dependencies. Every page is self-contained
(inline CSS, self-hosted Albert Sans), so it renders the same from `file://`
or any host.

## Run locally

    ruby -run -e httpd . -p 8000
    # open http://localhost:8000

Or just double-click `index.html`.

## Structure

    index.html                  Home
    case-studies/_template.html Copy this for each new case study
    assets/fonts/               Albert Sans 300 and 400, OFL licence
    assets/img/                 Screenshots (keep each under ~300 KB)

## Add a case study

1. `cp case-studies/_template.html case-studies/<slug>.html`
2. Replace every `[Replace: ...]` placeholder.
3. Add it to the work grid in `index.html`.

## Conventions

See `CLAUDE.md`.
