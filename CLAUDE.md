# CLAUDE.md

Personal portfolio for Chetan Shridhar, Principal UX Designer. The live
chetanshridhar.in is still the old WordPress site; this repo is its static
replacement. The current `index.html` is the approved design; new pages
follow it.

## Stack

- Plain static HTML and CSS. No build step, no package manager.
- Each page is self-contained: inline `<style>`, no external CSS. External
  requests are the font and one script.
- JavaScript is limited to Lenis 1.3.23 (smooth inertia scrolling, `lerp`
  0.104), loaded from jsDelivr with a pinned version and an SRI `integrity`
  hash, plus a short inline script. Lenis is off under reduced motion; touch
  and keyboard scrolling stay native; the menu and scroll hint glide via
  `lenis.scrollTo`, the name glides to the top; the skip link keeps its
  native jump. The inline script also runs the header (below) with plain
  scroll events. The page must work fully if Lenis fails to load.
- **Header**: scrolls away with the intro. Past it, the header gets a soft
  fade, `--bg` behind the name and menu dissolving to transparent below, with
  no border or hard edge (`.is-stuck`). It hides while scrolling
  down and slides back when scrolling up (`.is-hidden`), and returns to
  transparent at the very top. On phones the stuck bar is the logo mark and
  the menu on one line. Sticky section titles sit below it (`top:5.5rem`).
- Albert Sans (weights 200, 300, 400) loads from the Google Fonts CDN, with
  `display=swap` and a system sans-serif fallback.
- Ask before adding any library, other web font, script or framework.

## Files

    index.html                  Home: intro, selected work, building with AI, how I work, earlier work, experience, quotes, contact
    case-studies/_template.html Copy for each new case study (not yet restyled to match the home page)
    assets/img/                 Screenshots; JPEG, ~1200px wide, under ~300 KB each

## Preview

In the Claude app, start the "site" preview (defined in `.claude/launch.json`).
It serves the repo with the system Ruby, because `python3` on this Mac is the
Xcode stub. If port 8000 is busy, the app picks the next free one. From a
terminal:

    ruby -run -e httpd . -p 8000   # then open http://localhost:8000

## Design rules

- **Light, calm and classy.** Warm off-white page, near-black headings, warm
  grey text, hairline rules. Light mode only. No dark mode, gradients, glows,
  shadows, rounded cards, badges, pills, counters or marquees.
- **Motion on scroll, CSS only.** Scroll-driven animations
  (`animation-timeline`) inside `@supports` and
  `prefers-reduced-motion:no-preference`: the scroll hint fades out, the
  intro drifts slower than the page and fades, and screenshots pan gently
  inside their mats. Keep it slow and subtle; no reveal-on-scroll tropes.
- **Accent `#FF7722`, very sparingly.** Small marks only: Chetan's logo mark
  before his name in the header, the dot after the current role, link and nav
  hover underlines, the text selection tint. Never as a text colour (about
  2.7:1 on the page) and never as a fill or block.
- **Logo mark**: the petal shape from his logo SVG (the wordmark is not
  used), inline as `.mark`, 2rem wide, filled with `--accent`,
  `aria-hidden` because the name beside it is the link text.
- **Must not look AI-generated.** Avoid mono uppercase eyebrow labels, stat
  strips, "Let's talk"-style headlines, arrow-decorated links and buzzword copy.
- **References are inspiration, not templates.** Never reuse another site's
  layout, sentence pattern or signature technique (for example
  philipsamarets.com's intro line, accordion list or ASCII portrait).
- **No illustrations.** Typography, the grid, white space and Chetan's real
  screenshots carry the design. Each screenshot sits on a soft `--tile` mat
  (`.mat`) with no border or shadow. Do not draw or invent interface art,
  icons or decorative SVG.
- **Layout**: `.wrap` (max 80rem) holds a 12-column `.row`. Each section has
  a hairline on top, its title (`.lab`) in columns 1–3, sticky on desktop,
  and content (`.body`) in columns 4–12. Below 48rem everything stacks.
- **Type**: Albert Sans. Weight 200 for the headline; 300 for section titles,
  lead text, quotes and body; 400 for the name, nav, item titles and roles. Headline
  tracking −0.03em. Sentence case everywhere; hang opening quote marks.
- **Tokens** live in `:root` of each page's `<style>` (`--bg` #faf9f7,
  `--ink` #1c1b19, `--text` #4a4741, `--muted` #736e66, `--line` #e3dfd8,
  `--tile` #f0ede8, `--accent` #ff7722, `--sans`). Change a token in every
  page: `grep -rn -- "--accent" .`
- **CSS style**: compact one-line rules, short class names (`.wrap`, `.row`,
  `.lab`, `.mat`, `.xp`), `rem` units, mobile breakpoint at `max-width:48rem`.

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
