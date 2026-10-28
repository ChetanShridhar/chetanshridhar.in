# Portfolio site

Static site. No build step, no dependencies. Every page is self-contained
(inline CSS); the only external request is Albert Sans from Google Fonts.

## Run locally

    ruby -run -e httpd . -p 8000
    # open http://localhost:8000

Or just double-click `index.html`.

## Structure

    index.html                  Home
    case-studies/_template.html Copy this for each new case study
    assets/img/                 Screenshots (keep each under ~300 KB)

## Add a case study

1. `cp case-studies/_template.html case-studies/<slug>.html`
2. Replace every `[Replace: ...]` placeholder.
3. Add it to the work grid in `index.html`.

## Conventions

See `CLAUDE.md`.
