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
  scroll events and, on case studies, the Key views carousel (Previous/Next
  buttons, dots, arrow keys). The page must work fully if Lenis fails to load.
  On case study pages the menu links go to the home page, so Lenis doesn't
  intercept them.
- **Header**: scrolls away with the intro. Past it, the header gets a soft
  fade, `--bg` behind the name and menu dissolving to transparent below, with
  no border or hard edge (`.is-stuck`). It hides while scrolling
  down and slides back when scrolling up (`.is-hidden`), and returns to
  transparent at the very top. On phones the header is always one line: logo
  mark (1.5rem), name and menu, set a touch smaller, never wrapping. Nav links
  carry equal top and bottom padding so their text lines up with the name.
  Sticky section titles sit below it (`top:5.5rem`).
- Albert Sans (weights 200, 300, 400) loads from the Google Fonts CDN, with
  `display=swap` and a system sans-serif fallback.
- Ask before adding any library, other web font, script or framework.

## Files

    index.html                  Home: intro, designing AI / building with AI, selected work, how I work, earlier work, experience, quotes, contact
    case-studies/rule-builder.html  Web Security Rule Builder (Skyhigh Security): Chetan's own copy, verbatim apart from light grammar fixes
    case-studies/_template.html Copy for each new case study (not yet restyled to match the home page)
    assets/img/                 Screenshots; JPEG, ~1200px wide (covers up to ~1800px), under ~300 KB each
    assets/img/people/          Colleague photos for quote cards; square, 192px

## Preview

In the Claude app, start the "site" preview (defined in `.claude/launch.json`).
It serves the repo with the system Ruby, because `python3` on this Mac is the
Xcode stub. If port 8000 is busy, the app picks the next free one. From a
terminal:

    ruby -run -e httpd . -p 8000   # then open http://localhost:8000

## Design rules

- **Light, calm and classy.** Warm off-white page, near-black headings, warm
  grey text, hairline rules. Light mode only. No dark mode, gradients, glows,
  shadows, badges, pills, counters or marquees. Rounded corners only on the
  work and quote cards (6px), case study screenshot frames and diagram shapes
  (4–6px).
- **Motion on scroll, CSS only.** Scroll-driven animations
  (`animation-timeline`) inside `@supports` and
  `prefers-reduced-motion:no-preference`: the scroll hint fades out, the
  intro drifts slower than the page and fades, and screenshots on mats pan
  gently. Framed and laptop screenshots stay still. Keep it slow and subtle;
  no reveal-on-scroll tropes.
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
- **No decoration.** Typography, the grid, white space and Chetan's real
  screenshots carry the design. No invented interface art, icons or
  decorative SVG. On the home page each screenshot sits on a soft `--tile`
  mat (`.mat`) with no border or shadow.
- **Case study visuals**:
  - Cover: the main screen in a flat CSS laptop (`.device`: dark lid with a
    thin rim and camera dot, light base with a front lip and thumb notch), no
    mat behind it.
  - Screenshots: no mat, full width in a thin warm-grey rounded frame
    (`.shot`, `#5c5a56`). Blurred customer logos may be replaced with the
    company's real logo.
  - Diagrams: Chetan's own diagrams redrawn as inline SVG on a `--tile` mat,
    wording taken from his originals. They may use colour as a key (blue the
    product, green configurations, amber lists and values, the product's own
    action colours) and the product's parts (IF/AND tags, toggles). Wireframes
    are a calm Balsamiq-style sketch (`.bq`, light displacement filter, no
    extra font). Wide diagrams scroll sideways on phones with a "Swipe to see
    all of it" hint.
  - Several screens of one kind (Key views): a carousel (`.carousel`), one
    screen at a time, dots on the left, plain "Previous"/"Next" text buttons
    on the right.
- **Selected work** is cards, two per row (one on phones). Each card is
  white with 6px corners and no border: the stone image area runs to its
  edges, the text sits inside below it (`.txt`), and a 1px `--line` outline
  appears on hover. A thumbnail is a 4:3 crop of one telling detail of the real
  screen (`assets/img/*-detail.jpg`), never the whole mock-up. The crop
  starts at a real corner of the interface; on the `--tile` panel it is inset
  from that corner (`.thumb`, or `.thumb.tr` for top-right) and runs off the
  other edges, so it reads as framed, never bled into the page. It zooms
  slightly on hover. Confidential work gets a text-only card: label at the
  top, a large thin quote at the bottom.
- **AI comes first** after the intro: one lead line about skill and
  judgement, then two groups ("Designing AI", "Building with AI"), each with
  its subhead on the left and items in an aligned two-column grid. No
  headline numbers (not the 12 MCP apps), no loan sizes, and no company name
  in this section: talk about skill, scale and high-stakes decisions.
- **Company logos** (`assets/logos/*.svg|png`, clean copies; the original
  downloads sit in subfolders and are not committed) are shown in their own
  brand colours as plain `<img>`. Each gets an inline `height` set by eye so
  they weigh the same. HARMAN's "A Samsung Company" line is removed (Samsung
  bought it after Chetan left). Five logos (LIQUiDITY, Skyhigh Security,
  Akamai, HARMAN, Tesco) sit small under the intro summary, apart from the
  scroll hint, under a small grey "Worked for" title. Logos appear only there,
  not in Experience.
- **Experience**: one row per tenure with the company name on the right, in
  regular body weight (300) on desktop and phones. Titles
  held within the same tenure are nested in that row (current title first,
  earlier ones lighter); a return to a company later is its own row.
- **Colleague quotes**: white cards (6px), two per row, one on phones. The
  quote on top; at the bottom a small round greyscale photo, the name, then
  role and company (or role and date on a case study). An empty `--tile`
  circle stands in until a photo arrives.
- **No doubled rules**: a list of rows that opens a section drops its first
  top border, because the section's hairline is already there.
- **Contact**: one inviting lead line, then text rows (label left, link
  right) for email, LinkedIn, Dribbble, Medium, résumé and location. No phone
  number, no icon row, no oversized email address.
- **Layout**: `.wrap` (max 80rem) holds a 12-column `.row`. Each section has
  a hairline on top, its title (`.lab`) in columns 1–3, sticky on desktop,
  and content (`.body`) in columns 4–12. Below 48rem everything stacks. A
  long one-word title gets a `<wbr>` after its slash so it wraps.
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
  curly quotes and the `&copy;` entity. Quote colleagues verbatim (only fix
  missing spaces).
- **Case study copy is Chetan's own.** Keep his text and section order; fix
  grammar lightly, never rewrite or add copy of your own. List any wording
  change that touches meaning for him to confirm.
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
