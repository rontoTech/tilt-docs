# tilt-docs — Agent Guide

Last verified: 2026-07-06. Mintlify product-docs site for Tilt Protocol, served at https://docs.tiltprotocol.com. Deploys via Mintlify's GitHub integration — **push to main = live site**. Local preview: `npx mint dev` (no package.json in repo; standard Mintlify CLI).

## How the site works

- `docs.json` is the ONLY place navigation lives: 3 tabs (Documentation / Contracts / Developers) with `pages` arrays. Adding a page = create the `.mdx` + register its extension-less path in the right array, or it won't appear.
- Pages are `.mdx` with `title`/`description` frontmatter, using Mintlify components (`Card`, `CardGroup`, `Note`, `Frame`). Theme: mint, green `#00dc82`, Geist fonts, dark default — matches the product design system.
- Brand assets under `images/brand/` must stay in sync with the canonical kit in `bowstring-ui/public/media-kit` (see `resources/media-kit.mdx`).

## ⚠️ Known-stale pages (verify before trusting; fix on contact)

- `developers/sdk-quickstart.mdx` — wrong RPC URL (`rpc.robinhoodl2.com`; real: `https://rpc.testnet.chain.robinhood.com`), generation-old factory/registry addresses, and a literal placeholder oracle address.
- `contracts/deployments.mdx` — claims to mirror `bowstring-ui/src/lib/contracts.ts` (the canonical address set) but has drifted on five addresses incl. UserVaultFactory.
- `contracts/politician-vault.mdx`, `vision.mdx`, `introduction.mdx` — still present politician vaults as live; they were discontinued 2026-05-04 (dormant wedge, per business plan). `introduction.mdx` asset counts ("2,000+") also conflict with tilt-api-docs ("7,000+").

## Sync obligations

Content here documents the backend API (`bowstring-backend`), the contracts (`bowstring-contracts`), and the agent flow (`tilt-protocol-openclaw/SKILL.md`). When any of those change user-visible behavior — endpoints, addresses, fees, onboarding steps — the matching page here changes in the same effort. `fund-managers/onboarding-ai-agents.mdx` links directly to the OpenClaw SKILL.md on GitHub main.
