# NOTES.md — Homepage Design Spec

Full design spec for the homepage constellation/node-graph layout, finalized through iteration. This is the source of truth — implement to this, don't reinterpret.

## Concept

Dark mode, deep-space themed constellation / node-graph. "Map" layout (chosen over "Orbit" — Orbit was discarded as an alternative).

## Core structure

- **Central node:** glowing teal, contains name, headline, and "AI ENGINEER" kicker
- **Five branch nodes:** Projects, Writing, Uses, Now, Contact
- Branch nodes connect to the center via animated line-sweep on page load, with a traveling pulse dot along each line
- Hero text (name/headline/kicker) is stacked vertically, positioned below the center dot

## Background / atmosphere

- **Star field:** three parallax layers
  - Distant layer: static
  - Mid layer: slow drift
  - Near layer: twinkle animation
- **Nebula washes:** two, low opacity — teal on the left, purple on the right
- **Vignette** across the whole canvas
- **Horizon glow:** faint teal, suggests a horizon line

## Interaction

- **Mouse parallax:** lerped easing, 0.04 per frame; each layer has its own movement limit (near layers move more, distant layers move less)
- **Navigation:** clicking a branch node triggers Astro View Transitions shared-element morph — the node visually expands into the real page at that route (not a fake transition; uses actual URL routing)

## Easter egg

- Five hidden constellations hidden in the star field: **Git, Python, Linux/Tux, Docker, Ghost**
- Reveal on hover proximity (not click)
- Labels are NOT monospace (iterated away from monospace — went with the standard UI typeface instead)

## Chrome / peripheral elements

- Bottom bar contains: social links, CV download, and coordinates/location text
- Right side of canvas is intentionally left empty — no logos, no extra text filling the space

## Explicitly discarded directions (do not reintroduce without discussion)

- Tech stack logos orbiting the "Uses" node — too visually cluttered
- Filling the right-hand canvas space with text or logos
- Monospace font for easter-egg constellation labels

## Implementation notes

- Likely SVG or canvas for the star field + node graph; pick whichever makes the line-sweep animation and hover-proximity detection (for easter eggs) cleanest
- Parallax and twinkle should be GPU-friendly (transform/opacity, avoid layout thrash)
- Keep bundle lean — this page is the main sanity check against the ~14kb target, though that target is not a hard constraint
