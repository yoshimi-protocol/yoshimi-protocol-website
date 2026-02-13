# The Yoshimi Protocol Website

The Yoshimi Protocol is a community-ratified open framework for ethical AI development. This site hosts the landing page, the full Protocol document, and the public signatory list.

Repo: https://github.com/yoshimi-protocol/yoshimi-protocol-website
Live site: https://yoshimi-protocol.vercel.app (update if different)

## What is here
- `/` Landing page with principles, tiers, and sign-on call to action
- `/protocol` Full Protocol document rendered from Markdown
- `/signatories` Public signatory list rendered from a JSON data file

## Sign the Protocol
Signing is done via GitHub pull request. Fork the repo, add your entry to `src/data/signatories.json`, and open a PR. See `CONTRIBUTING.md` for step-by-step instructions.

## Development
```sh
npm install
npm run dev
```

## License
- Protocol text: CC0 1.0 Universal
- Website code: MIT
