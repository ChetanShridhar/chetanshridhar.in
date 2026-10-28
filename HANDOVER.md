# Handover: chetanshridhar.in portfolio

You're picking up the build of my portfolio site. A previous session set up the repo and built the home page. Separately, I worked on content and positioning in claude.ai. This handover combines both.

## Read first

1. **`CLAUDE.md`**: stack, design and content rules. It decides how the site is built and how it looks.
2. **`PORTFOLIO_BRIEF.md`**: who I am, what the site must achieve, my intent in my own words, facts per role, AI material, the case study template and open items. It decides what the site says.

If they conflict on design or tech, `CLAUDE.md` wins. Don't edit anything until you've read both and confirmed back to me, in a few lines, what you understood.

## Where things stand

**Setup**
- Plain static HTML/CSS, no build step, no JS. Roboto is self-hosted in `assets/fonts/`, so nothing external loads.
- Preview: the "site" config in `.claude/launch.json` runs on the system Ruby (`python3` on this Mac is only the Xcode stub). From a terminal: `ruby -run -e httpd . -p 8000`.
- **Nothing is committed yet.** Git has two earlier commits; everything since is uncommitted.

**How the design got here** (don't repeat these mistakes)
1. Dark theme, Geist and GSAP animations: rejected as too "AI-looking".
2. White with thin Roboto, based on my 2016–18 site: too bland.
3. Three drafts: I liked the editorial one, but the name was too big.
4. A version inspired by philipsamarets.com: it copied his layout too closely. That's why `CLAUDE.md` has the "references are not templates" rule.
5. **Current, approved direction:** my own interfaces redrawn as grey line art, each with one teal accent. Keep building on this.

**Home page (`index.html`)**
- **Intro:** a short line about me, then a drawing sheet of six strengths, each drawn from one of my interfaces (Vi3000, ViSi, Confer Control, Akamai regression testing, Rule Builder, Figma ↔ Storybook). It draws in once on load and swipes sideways on mobile.
- **Now:** my current AI work (fintech, underwriting, the AI-maintained design system, generative UI skills, MCP apps).
- **Work:** Rule Builder and Regression Testing, currently linking to the case studies on my old WordPress site. LIQUiDITY is marked confidential, with an email link to request a walkthrough.
- **Earlier work, 2012:** Vi3000, Confer Control, ViSi.
- **Experience:** roles from 2005 to now, drawn as a fader scale.
- **From colleagues:** quotes, word for word.
- **Contact:** email, résumé, LinkedIn, Abu Dhabi.
- Five screenshots are in `assets/img/`.

## Decisions already made (from my claude.ai planning)

- **Target:** full-time Principal or Staff IC first; Lead or UX Manager second. Fintech and cloud security first, but open to any domain. No consulting content, since I've only worked full-time.
- **AI is the headline:** both building AI products and using AI in my own work. Domains come second.
- **Before I share the site with a recruiter:** Rule Builder and Regression Testing must be live as case studies on *this* site, plus **at least one AI case study** (AI chat tool + MCP UIs at LIQUiDITY). My goal is two AI case studies. I'll write the AI content myself; you structure and build it.
- **Later:** the LIQUiDITY mobile app (end to end, 2025) to show mobile range.
- **Rule Builder and Regression Testing were written 4–5 years ago.** Rethink their flow using the template in `PORTFOLIO_BRIEF.md` §6. Don't just port them as they are.
- **Honesty:** no invented numbers, ever. Most of my work is 0→1. Show outcomes as what shipped, scope, real usage, decisions I made, quotes, and labelled estimates I can explain. One real number I can use: **12 complex MCP UIs built with Claude, where 2–3 was my realistic limit designing by hand in Figma.**
- **Self-taught:** I'm proud of it. Say it as a strength, never an apology.
- **Transparency:** add a short footer line saying the content is mine and the structure and flow were shaped with AI (wording to confirm with me). I also want my handwritten questionnaire answers available somewhere as a source of truth.
- **Personality:** show it through how the stories are told (calm, product first, credit to the team, no blame), never through adjectives.

## Tasks, in order

Propose each step and wait for my OK before editing.

1. **Baseline commit:** suggest a commit message for the current state. Commit only when I say so.
2. **Fix `README.md`:** it still says the site uses system fonts and suggests `python3`.
3. **Restyle `case-studies/_template.html`** to match the home page and follow the structure in `PORTFOLIO_BRIEF.md` §6.
4. **Rule Builder case study:** I'll provide the old content and images. Propose a restructured flow first, then build it, and point the home page link at the new page instead of WordPress.
5. **Regression Testing case study:** same approach.
6. **AI case study page (AI chat tool + MCP UIs):** build the structure with `[Replace: …]` placeholders from `PORTFOLIO_BRIEF.md` §4 while I write the content.
7. **Confirm with me:** the strength labels (especially "User research"), the year of the Akamai regression tool, and HARMAN 2013–14 versus the "2012" section label.
8. **Hosting:** moving off WordPress to static hosting with the `chetanshridhar.in` domain. Plan only. Nothing happens without my approval.

## Conflicts and decisions to raise with me

- **LIQUiDITY is marked "confidential"** on the home page, but I plan to publish AI case studies from it. Before building those pages, help me decide what can be public (generic architecture wording, recreated or blurred screens). Internal terms like op-runner, knowledge graph or ontology layer and GraphQL need my sign-off.
- **Contact form vs. the no-JS rule:** a static site can't send a form without a third-party service. Lay out the options (a plain email link, or a form service such as Formspree or Netlify Forms) and let me choose.
- **About / How I work with AI / Source notes:** `PORTFOLIO_BRIEF.md` suggests these as pages. The current home page covers some of it under "Now". Propose whether they become separate pages or stay sections.

## What every case study must make clear

A review of my material showed three gaps hiring managers will probe. Help me close them in every case study:
1. **Decisions I owned**, not just that I was involved. Name two or three of my own calls per project.
2. **How it was validated** with users, especially work I built quickly with AI.
3. **How success was judged**, even without hard metrics.

Also show at least one trade-off where business or engineering won over a UX principle, and how I flagged the caveat. That is my approach, and it should be visible.

## Reminders I asked for

- When we build the AI pages, ask me for **research examples** that support the "black box" point (AI drifting from the design system on fast projects).
- My "random check questions" example (designing against AI complacency in lending) is unfinished in my notes. Ask me for the full version.
