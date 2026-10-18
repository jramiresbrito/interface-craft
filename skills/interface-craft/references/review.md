# Review and the final check

Use this on your own work before you hand it back (Build), and on someone else's (Review). Mark each line **pass**, **fail** with the fix, or **not verified** with the reason.

## How to look

1. Open it in a real browser (headless Chromium is fine).
2. Screenshots at 390 and 1440 px, light and dark, and one width in between (about 900 px).
3. Read the console after load and after each action.
4. Use it with the keyboard only.
5. Zoom to 200 %: nothing overlaps or is cut off.
6. Turn on reduced motion and look again.
7. Fill it with the longest real values and with nothing (see `break.md`).

## The checklist

**Structure**
- [ ] The main idea is clear in the first viewport.
- [ ] Headings in order, one `h1`, a "Skip to content" link.
- [ ] Every state designed: regular, empty, error, loading; stale and offline for live data.

**Visual**
- [ ] All colours from tokens; both schemes exist and were seen.
- [ ] Body text 4.5:1 or more; meaningful labels readable, not the lightest grey.
- [ ] One accent; status colours mean status; never meaning by colour alone.
- [ ] Reading text 60–75 characters a line; balanced headings.
- [ ] No horizontal page scroll at 390 px; long ids wrap.
- [ ] Tabular numbers; one precision per column.
- [ ] It does not look like a default template.

**Interaction**
- [ ] Everything works by keyboard with a visible focus ring.
- [ ] Targets 24 px+ (44 px touch); no dead zones; `<a>` navigates, `<button>` acts.
- [ ] Tabs, filters and open panels in the URL; stable anchors.
- [ ] Hover only under a hover media query; 16 px inputs on phones; `100dvh` shells.
- [ ] Loading never flashes; destructive actions confirm or undo.

**Motion**
- [ ] Frequent actions have no animation.
- [ ] No `transition: all`, no `ease-in`, nothing over 300 ms, nothing from `scale(0)`.
- [ ] Only `transform` and `opacity` animate.
- [ ] Reduced motion removes movement and keeps fades.

**Diagrams**
- [ ] Mermaid pinned to an exact current version, shown at 100 % on load, vector zoom, a caption (`diagrams.md`).

## The review format

Start with the issues, worst first, as a table:

| # | Before | After | Why |
|---|---|---|---|
| 1 | `transition: all 400ms ease-in` on the menu | `transition: opacity 150ms ease-out, transform 150ms ease-out` | Named properties; menus open often; ease-in feels late |

Then the checklist, the screenshots by name, and "Not verified".
