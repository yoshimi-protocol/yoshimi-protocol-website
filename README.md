# Yoshimi Protocol — Website

This is the source code for [yoshimiprotocol.org](https://yoshimiprotocol.org), the public-facing website for the Yoshimi Protocol.

The website presents the Protocol document, explains the certification tiers, and hosts the public signatory list. It is a static content site — no database, no authentication, no backend.

**For the Protocol itself** — the founding document, certification framework, compliance templates, and governance — see the [protocol repo](https://github.com/yoshimi-protocol/protocol).

---

## Tech Stack

- **Framework:** [Astro](https://astro.build) with TypeScript
- **Styling:** Tailwind CSS
- **Hosting:** [Vercel](https://vercel.com)
- **Content:** Markdown rendered at build time

## Local Development

```bash
git clone https://github.com/yoshimi-protocol/yoshimi-protocol-website.git
cd yoshimi-protocol-website
npm install
npm run dev
```

The dev server runs at `http://localhost:4321` by default.

## Project Structure

```
src/
├── components/      # Reusable UI components
├── content/         # Protocol markdown content
├── data/
│   └── signatories.json  # Signatory registry
├── layouts/         # Page layout templates
├── pages/           # Astro page routes
│   ├── index.astro  # Landing page
│   ├── protocol.astro  # Full Protocol document
│   └── signatories.astro  # Public signatory list
└── styles/          # Global styles
public/              # Static assets (favicon, images, etc.)

```

## Signatory Data

The signatory list at `/signatories` is rendered from `src/data/signatories.json` at build time. When someone signs the Protocol, they add an entry to this file via pull request.

Signing instructions and the full process are documented in the protocol repo's [CONTRIBUTING.md](https://github.com/yoshimi-protocol/protocol/blob/main/CONTRIBUTING.md).

## Deployment

The site deploys automatically to Vercel on push to `main`. The custom domain `yoshimiprotocol.org` is configured through Vercel's dashboard.

## Contributing to the Website

Contributions to the website itself — design improvements, bug fixes, accessibility, performance — are welcome. Open an issue first to discuss, then submit a PR.

This is separate from contributing to the Protocol, which happens in the [protocol repo](https://github.com/yoshimi-protocol/protocol).

## License

- **Website code:** MIT
- **Protocol text:** CC0 1.0 Universal — belongs to no one and therefore to everyone.
