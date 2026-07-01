# CLAUDE.md — anujmali.com.np

Project context for Claude Code. Read this before making changes.

## Stack (decided, don't relitigate)

- **Framework:** Astro, static output (`output: 'static'` in astro.config.mjs)
- **Styling:** Tailwind CSS v4 via `@tailwindcss/vite` (NOT `@astrojs/tailwind` — that's deprecated for v4). No `tailwind.config.mjs`; theme tokens go in `src/styles/global.css` under `@theme { ... }`.
- **Deployment:** Cloudflare Pages (build command `npm run build`, output dir `dist`)
- **Navigation:** Astro View Transitions (`<ViewTransitions />`) for shared-element morph between homepage nodes and their target pages

## Pages (5 total)

1. `/` — home (constellation node-graph, see NOTES.md for full spec)
2. `/projects`
3. `/writing`
4. `/uses`
5. `/now`

## Blogging

- Git-based markdown files inside this repo (no CMS)
- Canonical source = this site; cross-post to Dev.to and Hashnode for distribution
- Target: 3–4 published technical posts by end of 2026

## Working principles

- **Simplicity wins.** When in doubt, remove rather than add. Don't introduce visual approaches that mix metaphors (e.g. discarded: tech logos orbiting a node — too cluttered).
- **No speculative overhead.** Don't add tooling, abstractions, or config for problems that don't exist yet.
- **Just-in-time learning.** If something requires learning a new concept, learn it as the problem comes up — don't front-load unrelated research.
- Prefer one concrete implementation over presenting multiple options, unless a real tradeoff exists.
- Direct, concise communication. Push back if a suggestion feels overbuilt or off from the design spec.

## Current state

- Astro project scaffolded, Tailwind v4 installed and wired via Vite plugin
- `src/styles/global.css` created by the Astro CLI
- Shared layout (`src/layouts/Base.astro` or similar) NOT yet created — this is the next step, and must import `global.css` and include `<ViewTransitions />`
- Five route files not yet stubbed
- Homepage visual design is fully specced (see NOTES.md) but not implemented

## Immediate next steps

1. Build `src/layouts/Base.astro` (imports global.css, ViewTransitions, dark-mode base shell)
2. Stub the five page files, each using the shared layout
3. Implement the homepage constellation/node-graph per NOTES.md
