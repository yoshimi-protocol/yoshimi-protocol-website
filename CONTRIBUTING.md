# Contributing to the Yoshimi Protocol Website

Thanks for your interest in improving the website. This guide covers contributions to the **website codebase** — the design, code, and infrastructure that powers [yoshimiprotocol.org](https://yoshimiprotocol.org).

**Looking to contribute to the Protocol itself?** That happens in the [protocol repo](https://github.com/yoshimi-protocol/protocol). Signing, amendments, compliance challenges, and governance discussions all live there.

---

## What We Welcome

- Bug fixes and broken link reports
- Accessibility improvements
- Performance optimizations
- Design refinements and responsive layout fixes
- Documentation improvements for this repo
- New features that serve the Protocol's mission (discuss first)

## How to Contribute

1. **Open an issue first** for anything beyond a trivial fix. Describe what you'd like to change and why.
2. **Fork the repo** and create a branch from `main`.
3. **Make your changes.** Run the site locally to verify everything works:
   ```bash
   npm install
   npm run dev
   ```
4. **Submit a pull request** against `main` with a clear description of what changed.

## Signatory PRs

Adding yourself to the signatory list is done by editing `src/data/signatories.json` in this repo. However, the signing process, requirements, and instructions are documented in the protocol repo's [CONTRIBUTING.md](https://github.com/yoshimi-protocol/protocol/blob/main/CONTRIBUTING.md). Please follow those instructions.

## Project Structure

The site is built with [Astro](https://astro.build) and styled with Tailwind CSS. Key locations:

- `src/pages/` — Page routes (landing, protocol, signatories)
- `src/components/` — Reusable UI components
- `src/content/` — Protocol markdown content rendered at build time
- `src/data/signatories.json` — Signatory registry
- `src/layouts/` — Page layout templates
- `src/styles/` — Global styles
- `public/` — Static assets

## Guidelines

- Keep PRs focused. One concern per PR.
- Test locally before submitting.
- Follow existing code style and conventions.
- The Protocol text rendered on the site should match the canonical version in the [protocol repo](https://github.com/yoshimi-protocol/protocol/blob/main/PROTOCOL.md). Do not edit Protocol content through this repo.

## Code of Conduct

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md). By participating, you agree to uphold it.
Steps:
1. Fork this repo.
   - GitHub docs: https://docs.github.com/en/get-started/quickstart/fork-a-repo
2. In your fork, open `src/data/signatories.json`.
3. Add your entry at the end of the array using the same format as the existing entries.
4. Commit your change.
5. Open a pull request back to the main repo.
   - GitHub docs: https://docs.github.com/en/pull-requests

Why this approach:
- Privacy-first: no forms or hidden databases
- Anti-spam: requires a GitHub account and review
- Transparent: public, version-controlled record
- Community-owned: anyone can fork and verify
- Aligned with the Protocol's governance values

## 2) Contribute to the Protocol document
Amendments are community-governed. Please open an issue first to discuss changes, then submit a PR that references the issue.

Governance and amendment rules are defined in the Protocol document (Part VIII: Governance). Please read that section before proposing changes.

## Code contributions
If you want to improve the site, open an issue and describe the change. Small fixes can go directly to a PR.

## Code of Conduct
By participating, you agree to abide by the Code of Conduct in `CODE_OF_CONDUCT.md`.
