# Project Setup & MVP — The Yoshimi Protocol Website

## Overview
Create the website for the Yoshimi Protocol — a community-ratified open framework for ethical AI development. The site serves three purposes: (1) present the Protocol document itself, (2) act as the public landing page and call-to-action for the initiative, and (3) host the signatory list of developers and organizations who have pledged to follow the Protocol.

This is primarily a **content site**, not an application. Optimize for speed, readability, and professionalism. The tone is warm but serious — editorial, not corporate.

## Tech Stack
- **Framework:** Astro (latest stable) with TypeScript
  - Astro is chosen because this is a content-first site with minimal interactivity. It ships zero JS by default, renders static HTML, deploys to Vercel, and is ideal for presenting long-form documents beautifully.
  - If for any reason Astro presents issues, fall back to Next.js (App Router, TypeScript) with static export.
- **Styling:** Tailwind CSS
- **Fonts:** Load from Google Fonts — `IBM Plex Mono` for labels/code, `Inter` or `DM Sans` for body, `Bebas Neue` or similar bold condensed for display headings. Reference the existing landing page HTML for the typographic hierarchy.
- **Hosting:** Vercel (I will connect the repo)
- **License:** CC0 1.0 Universal (the Protocol itself), MIT for the website code
- **No database.** No Supabase. No backend. Fully static.

## Repository Setup
- Initialize a git repo named `yoshimi-protocol`
- Include: `.gitignore`, `LICENSE` (MIT for code), `README.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`
- The README should briefly explain the project, link to the live site, and explain how to sign on (via PR — see Signatory System below)
- The CONTRIBUTING.md should explain two contribution paths:
  1. **Signing the Protocol** — fork the repo, add yourself to the signatory file, open a PR
  2. **Contributing to the Protocol itself** — open an issue for discussion first, then PR against the Protocol document. Amendments follow the process described in the Protocol (Part VIII: Governance).

## Design Direction
An existing HTML landing page has been built and should be used as **design reference and inspiration** — not ported verbatim. The key design characteristics to preserve:

- **Dark theme** — deep blacks/dark blues (`#0a0a0f` range), with warm amber/gold accents and a muted pink accent (the "pink robots" nod)
- **Editorial typography** — large bold headlines, generous whitespace, readable body text
- **Scrolling marquee** with principle teasers (subtle, not distracting)
- **Section structure:** Hero → Origin Story ("Why Yoshimi?") → Principles overview → Certification Tiers → Sign the Protocol CTA → Open Source callout → Footer
- **No stock imagery.** Typography and layout do the heavy lifting.
- The tone walks a line: it references the Flaming Lips album *conceptually* (a warrior battling robots, "she's taking her vitamins," the spirit of the album) but never quotes lyrics or reproduces copyrighted material. The association is *implied*, not explicit.

## Site Architecture

| Route | Description |
|---|---|
| `/` | Landing page — hero, origin story, principles overview, tiers, CTA to sign, open source section |
| `/protocol` | The full Yoshimi Protocol document rendered beautifully as a long-form page with a sticky table of contents sidebar for navigation (Parts I–IX, Glossary, Closing Statement) |
| `/signatories` | Public list of all signatories, rendered from a data file in the repo |

That's it for MVP. Three pages. Keep it tight.

### Future pages (do NOT build these, just be aware of them for architecture decisions):
- `/badges` — badge assets and usage instructions (coming soon)
- `/blog` — updates and announcements
- `/governance` — detailed governance procedures

## Page Details

### Landing Page (`/`)
Reference the existing HTML landing page for structure and tone. Key sections:

1. **Hero** — Bold headline: "The Yoshimi Protocol". Subheadline: "A community-ratified framework for AI developers who want the world to know they're building for us — not against us." Two CTA buttons: "Read the Protocol" (→ `/protocol`) and "Sign the Protocol" (→ scrolls to sign-on section or links to GitHub).
2. **Scrolling marquee** — Principle teasers cycling horizontally. Subtle, monospaced, uppercase.
3. **Origin Story** — "Why Yoshimi?" section. A warrior. Pink robots. The spirit of the name. Keep it punchy — 2-3 paragraphs max.
4. **Five Core Principles** — Grid or card layout. Each principle from the Protocol summarized in 1-2 sentences. These are teasers — the full text lives on `/protocol`.
5. **Three Certification Tiers** — Cards for Acknowledged, Compliant, and Verified. The Compliant card should be visually featured (it's the sweet spot). Include the taglines from the existing HTML. **Add a note on the Badges section: "Badge assets — Coming soon."**
6. **Sign the Protocol CTA** — This section should direct users to GitHub, NOT collect data via a form. Explain the PR-based sign-on process clearly and concisely:
   - "Signing the Yoshimi Protocol is a public act. Fork the repo, add your name, open a pull request."
   - Link to the GitHub repo
   - Link to `CONTRIBUTING.md` for detailed instructions
   - Explain that this approach is intentional: no hidden databases, no data collection, full transparency — you choose exactly what to share.
7. **Open Source section** — Brief statement that the Protocol is CC0, the code is MIT, and the community owns this.
8. **Footer** — Links to GitHub repo, `/protocol`, `/signatories`. No social media links for now.

### Protocol Page (`/protocol`)
- Render the full Protocol document (PROTOCOL.md) as a beautifully typeset long-form page
- **Sticky sidebar table of contents** on desktop that highlights the current section as the user scrolls (use Intersection Observer — this is one place where a small JS island is justified in Astro)
- On mobile, collapse the TOC into a dropdown or hamburger at the top of the page
- The Protocol source content is provided below. Store it as a markdown file (`src/content/protocol.md`) and render it with Astro's built-in markdown support or a markdown rendering library.
- Typography should be optimized for long-form reading: ~65-75 character line width, generous line height (1.7+), clear heading hierarchy
- The document has these major sections — each should be its own TOC entry:
  - Preamble
  - Part I: Why This Moment Is Different
  - Part II: Tier One Commitments (Eternity Clauses)
  - Part III: Tier Two Principles (Structural)
  - Part IV: Tier Three Principles (Operational)
  - Part V: On AI Welfare and Moral Status
  - Part VI: The Horizon Clause
  - Part VII: Amendment
  - Part VIII: Governance
  - Part IX: Certification
  - Glossary
  - Closing Statement

### Signatories Page (`/signatories`)
- Renders a public list of all signatories from a data file in the repo
- Use a JSON or YAML file as the data source: `src/data/signatories.json` (or `.yaml`)
- Each signatory entry contains:
  ```json
  {
    "name": "Andy Haight",
    "github": "athaight",
    "organization": "Independent",
    "tier": "acknowledged",
    "date": "2026-02-13",
    "project": "optional — name of the AI project being pledged"
  }
  ```
- Display as a clean table or card grid, sortable/filterable by tier
- Include me (Andy Haight) as the first signatory as seed data
- Header text should explain what this list represents and link to the sign-on instructions

## Signatory System — The GitHub PR Approach
This is critical to get right. The sign-on process is:

1. A developer or org visits the site, reads the Protocol
2. They decide to sign → the site directs them to GitHub
3. They fork the repo, edit `src/data/signatories.json`, add their entry to the array
4. They open a PR with their addition
5. A maintainer (me, initially) reviews and merges

**Why this approach (document this in CONTRIBUTING.md):**
- **Privacy-first:** No data collection on the website. No forms. No email harvesting. Signatories share exactly what they choose to share in their PR.
- **Anti-spam:** Requires a GitHub account and a PR review. Natural quality filter.
- **Transparent:** The entire signatory list is version-controlled and publicly auditable.
- **Community-owned:** Anyone can fork. No single entity controls the data.
- **Matches the Protocol's values:** The sign-on mechanism itself embodies the transparency and community governance the Protocol advocates.

The CONTRIBUTING.md should include step-by-step instructions with links to GitHub's docs on forking and PRs, so that less technical signatories can follow along.

## Protocol Document Content
The full Protocol document (PROTOCOL.md) has already been written. I will provide this file separately and place it in the repo at `src/content/protocol.md`. **Do not write or generate the Protocol content — it already exists.** Just set up the rendering infrastructure to display it beautifully.

For scaffolding purposes, create a placeholder `src/content/protocol.md` with a note: `<!-- Protocol content will be placed here. See PROTOCOL.md in the repo root. -->` and also copy it to the repo root as `PROTOCOL.md` for GitHub rendering.

## Constraints
- No database. No backend. No Supabase. No API routes. Fully static site.
- No form-based sign-on. All sign-ons happen via GitHub PRs.
- No badge assets yet — just a "Coming soon" note in the tiers section.
- No blog, no governance page, no additional pages beyond the three defined above.
- Do not generate or modify the Protocol document content — only set up the infrastructure to render it.
- Do not include any direct quotes from Flaming Lips lyrics or any copyrighted material. The cultural reference is implied through the name and the "warrior battling robots" framing only.
- Ship something clean and functional. Pixel-perfect polish can come later — but the typography and reading experience on the `/protocol` page should be genuinely good from the start, as the document IS the product.
- Use semantic HTML throughout. The Protocol page especially should be accessible and screen-reader friendly.

## Definition of Done
1. `yoshimi-protocol` repo initialized with proper scaffolding, license files, README, CONTRIBUTING, and CODE_OF_CONDUCT
2. Landing page renders with hero, origin story, principles, tiers, GitHub sign-on CTA, and footer
3. `/protocol` page renders the markdown document with a sticky TOC sidebar that highlights on scroll
4. `/signatories` page renders the signatory list from the JSON data file, with me as the first entry
5. The site builds and deploys successfully to Vercel as a static site
6. `CONTRIBUTING.md` clearly explains both the PR sign-on process and the Protocol amendment process
7. The overall aesthetic matches the dark, editorial, typography-forward tone described above
