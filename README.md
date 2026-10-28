# Portfolio site

Static site. No build step, no dependencies. Every page is self-contained
(inline CSS, system fonts), so it renders the same from `file://` or any host.

## Run locally

    ruby -run -e httpd . -p 8000
    # open http://localhost:8000

`python3 -m http.server 8000` also works once Xcode command line tools are
installed. Or just double-click `index.html`.

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
