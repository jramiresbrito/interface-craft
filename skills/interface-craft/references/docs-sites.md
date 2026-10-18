# Documentation and reading sites

From a study of Mintlify, Fumadocs, Stripe Docs, Tailwind CSS, Astro Starlight and Vercel docs; Diátaxis; Meng, Steinhardt and Schubert, "How Developers Use API Documentation" (2019); the New Relic docs style guide; Bikeshed and ReSpec.

## Two kinds of reader

Developers spend about half their time reading. Systematic readers want an overview first; opportunistic readers search, jump and copy. Serve both: an Overview page and a menu that shows the shape of the system, plus instant search and stable anchors to every heading and item.

## The frame

- **Three columns:** menu, text, "On this page". Drop the right column under about 1240 px; put the menu behind a button under about 860 px.
- **Two navigation levels:** tabs at the top for the big sections, a left tree for the pages of the current section.
- **A project or product switcher** at the top.
- **Groups of seven items or fewer;** groups fold; the current item has a tinted background and the accent colour.
- **Search in the header** with the shortcut shown (Ctrl K and `/`). The palette opens instantly (no animation), groups results by kind, moves with arrows, opens with Enter, highlights the match.
- **Right column:** "On this page" from the headings, a thin rail marking the current section as you scroll; below it, a small card of page facts.

## The page

- Breadcrumbs, a title of about 34–40 px semibold, then one description line in the secondary colour.
- **Page actions** under the title: Copy as Markdown, open the source, copy the link.
- A tinted callout only when something needs attention.
- Segmented tabs for variants of the same content.
- Figures in a frame with a caption that states the claim (see `diagrams.md`).
- Previous and next at the end; the source path and the last change under them.

## Keep kinds of text apart (Diátaxis)

Tutorial (learn by doing), how-to (a task), reference (facts), explanation (why). Do not mix them on one page; link between them.

## Specifications and requirements

- Every requirement and scenario has a stable id and anchor (R3, R3.S2).
- Terms link to their definitions; a glossary lists them.
- Trace both ways: a requirement shows its tests; a missing test shows as "no test found" in the bad colour, never hidden.
- Scenarios read as WHEN / THEN / AND with the keywords as tinted chips and the text at full contrast.
- Show which change added or changed each requirement, with the date.

## What the best ones do not do

No pattern behind the text, no decorative gradients, no animation on page load, no content lighter than the secondary colour, no second accent colour.
