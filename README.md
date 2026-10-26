# Portfolio site

Static site. No build step, no dependencies. Every page is self-contained
(inline CSS, system fonts), so it renders the same from `file://` or any host.

## Run locally

    python3 -m http.server 8000
    # open http://localhost:8000

Or just double-click `index.html`.

## Structure

    index.html                  Home: intro, selected work, about, contact
    case-studies/_template.html Copy this for each new case study
    assets/                     Images, PDFs (keep each image under ~300 KB)

## Add a case study

1. `cp case-studies/_template.html case-studies/<slug>.html`
2. Replace every `[Replace: ...]` placeholder.
3. Link it from the "Selected work" list in `index.html`.

## Conventions

- Design tokens live in `:root` at the top of each page's `<style>`. If you
  change a color or type size, change it in every page (search for `--accent`).
- Placeholder copy is always wrapped as `[Replace: ...]` so it is greppable:
  `grep -rn "Replace:" .`
