# Visual design

From Refactoring UI, the Vercel Web Interface Guidelines, the visual-explainer skill, a study of six documentation products (Mintlify, Fumadocs, Stripe, Tailwind, Starlight, Vercel) and a production trading-platform design system.

## Tokens first

- Every colour is a custom property on `:root`. Components use role names (`--fg`, `--fg-2`, `--bg-subtle`, `--accent`), never a raw hex value.
- Two tiers: raw values feed role names; dark mode changes the raw values only.
- A page that lives ships both schemes: the dark set under `@media (prefers-color-scheme: dark)` guarded by `:root:not([data-theme="light"])`, and again under `:root[data-theme="dark"]` for a manual toggle. Pick dark values by eye; never invert.
- Set `color-scheme` (`light dark`, or `dark` in the dark set) and one `<meta name="theme-color">` per scheme.

## Colour

- **One accent.** The best documentation products use one accent colour. Status colours (ok, warn, bad, info) are separate from the accent and only mean status.
- **Tuned neutrals.** A pure mid grey looks unconsidered; use a tuned scale (zinc, slate) or bias the greys toward the accent hue.
- **Three text levels:** primary (headings, values), secondary (body), tertiary (metadata). A fourth, lighter level only for disabled or decorative text - never for a label that carries meaning.
- **Text on a coloured surface** is a colour of the same hue with other saturation and lightness, not grey. Borders and shadows on a tinted surface are tinted too.
- **Measure every colour.** A reused palette is not a measured palette (a common red, `#E53935`, is only 4.23:1 on white and fails small text). Body text 4.5:1, large text and UI parts 3:1. APCA is a better model when you can use it.
- **Interactive states** (hover, active, focus) have more contrast than the rest state.

## Type

- One font pair: a sans for text and a mono for code, ids and numbers. Good pairs: Geist + Geist Mono, IBM Plex Sans + IBM Plex Mono, DM Sans + Fira Code. A display face only for a few large titles on editorial pages.
- Load every weight the CSS uses (no faux bold); preconnect to the font host or self-host.
- A rem scale with one root knob (`html { font-size: 16px }`). Body 15 to 17 px, never below 14 px; labels 11 px or more; code 12 px or more.
- Headings: semibold, about −0.02em letter spacing at large sizes, `text-wrap: balance`. Body: `text-wrap: pretty`.
- Measure: 60 to 75 characters (`max-width: 65ch` to `72ch`), line height 1.6 to 1.7 for reading, 1.4 to 1.5 for UI.
- Uppercase labels: small, letter spacing +0.04 to +0.08em, and only when they classify something.
- Details: curly quotes, the ellipsis `…`, a non-breaking space between a number and its unit, `tabular-nums` for compared numbers.

## Space and layout

- A spacing scale (4, 8, 12, 16, 24, 32, 48, 64 px). Space siblings with `gap`, not collapsing margins.
- More space between groups than inside a group.
- Align to a grid, a baseline or an edge; correct optical alignment by 1 px when the eye says so.
- Prevent overflow: `min-width: 0` on grid and flex children, `overflow-wrap: anywhere` for ids, hashes and paths, a scroll container for wide tables and code.
- Concentric radii: a child radius is equal to or less than its parent radius.

## Depth

- Structure with thin borders and 1 px rings. Keep the layered shadow for overlays (menus, dialogs, the command palette).
- A real shadow has two layers: ambient and direct.
- One elevated thing at a time.

## The generic look (avoid unless asked)

- Inter or system-ui as the only font with no thought; violet or fuchsia as the main accent; purple-to-blue gradient heroes; gradient mesh blobs; neon cyan-magenta dashboards.
- Emoji section markers; centred everything; the same large radius on every box; an accent bar on every card.
- 01 / 02 / 03 markers when order does not matter; eyebrow labels that classify nothing.

Test: put the page next to a default template. If you cannot tell them apart, it is not done.

## Anchor the look in the content

Choose the direction from the subject: documentation → quiet product docs; infrastructure and CLI → terminal; metrics → dense data; architecture → blueprint; recaps → editorial. Write the direction in one sentence before you pick colours.
