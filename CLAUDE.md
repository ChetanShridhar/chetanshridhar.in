# CLAUDE.md

Personal portfolio for Chetan Shridhar, Principal UX Designer. The live
chetanshridhar.in is still the old WordPress site; this repo is its static
replacement. The 2016–2018 hand-built site (white, Roboto light, teal accent)
is the visual reference.

## Stack

- Plain static HTML and CSS. No build step, no package manager, no JavaScript.
- Each page is self-contained: inline `<style>`, no external CSS, fonts or
  scripts. Pages must render the same from `file://` or any host.
- Roboto (weights 100, 300, 400, 500, latin) is self-hosted in `assets/fonts/`
  from @fontsource/roboto 5.0.13; Apache licence beside it.
- Ask before adding any library, other web font, script or framework.

## Files

    index.html                  Home: intro + drawing sheet, now, work, earlier work, experience, quotes, contact
    case-studies/_template.html Copy for each new case study (not yet restyled to match the home page)
    assets/img/                 Screenshots; JPEG, ~1200px wide, under ~300 KB each

## Preview

In the Claude app, start the "site" preview (defined in `.claude/launch.json`).
It serves the repo with the system Ruby, because `python3` on this Mac is the
Xcode stub. If port 8000 is busy, the app picks the next free one. From a
terminal:

    ruby -run -e httpd . -p 8000   # then open http://localhost:8000

## Design rules

- **Plain and white.** White background, grey text, one teal accent
  (`#2d9695`). No dark mode, gradients, glows, shadows, rounded cards, badges,
  pills, counters, marquees or scroll-triggered animations.
- **Must not look AI-generated.** Avoid mono uppercase eyebrow labels, stat
  strips, "Let's talk"-style headlines, arrow-decorated links and buzzword copy.
- **References are inspiration, not templates.** Never reuse another site's
  layout, sentence pattern or signature technique (for example
  philipsamarets.com's intro line, accordion list or ASCII portrait).
- **Visual language: Chetan's own interfaces as line art.** Drawings are
  inline SVG redrawn from his real screens (Vi3000 strips, ViSi EQ curve and
  fader, Confer Control seats, Akamai test list, Rule Builder rows, Figma ↔
  Storybook). Grey `--draw` strokes, one teal element per fragment, captions
  naming the source. The intro has a chronological drawing sheet that draws
  in once on load (CSS only, off under reduced motion); each section header
  has a small fragment on the right; Experience is drawn as a fader scale.
- **Type**: Roboto, thin. Name, section titles and lead text weight 100; body
  300; item titles, nav and captions 400.
- **Tokens** live in `:root` of each page's `<style>` (`--bg`, `--ink`,
  `--text`, `--muted`, `--line`, `--tile`, `--accent`, `--draw`, `--sans`).
  Change a token in every page: `grep -rn -- "--accent" .`
- **CSS style**: compact one-line rules, short class names (`.wrap`, `.work`,
  `.scale`), `rem` units, mobile breakpoint at `max-width:48rem`.

## Content rules

- **Copy**: less is more. First person, one line per idea, no filler. Use
  curly quotes and the `&copy;` entity. Quote colleagues verbatim.
- **Placeholders** are always written as `[Replace: ...]` so they stay
  greppable: `grep -rn "Replace:" .` Never invent copy, metrics, dates, roles
  or outcomes to fill one; leave it and tell me.
- **Accessibility**: keep the skip link, `aria-labelledby` on sections,
  visible `:focus-visible` outlines, meaningful `alt` text on every image, one
  `<h1>` per page.

## Adding a case study

1. `cp case-studies/_template.html case-studies/<slug>.html`
2. Replace every `[Replace: ...]` placeholder.
3. Add it to the work grid in `index.html`.

## Working with me

- Propose changes and wait for approval before editing; read-only tasks first.
- Do not commit or push unless asked.
