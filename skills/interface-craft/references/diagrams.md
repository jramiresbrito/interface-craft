# Diagrams (Mermaid)

Old Mermaid versions and default settings give tiny, blurry text that breaks when you zoom. These rules come from a system map that renders 25 diagrams well, and from the visual-explainer skill.

## Version and settings

- Pin an exact current version: `import mermaid from "https://cdn.jsdelivr.net/npm/mermaid@12.1.0/dist/mermaid.esm.min.mjs"` (or self-host the same file).
- ```js
  mermaid.initialize({
    startOnLoad: false, securityLevel: "strict", theme: "base", fontSize: 15,
    fontFamily: "<the page body font>",
    themeVariables: { /* from the page tokens */ },
    flowchart: { useMaxWidth: false, htmlLabels: true, curve: "basis",
                 nodeSpacing: 40, rankSpacing: 50, padding: 12, wrappingWidth: 320 },
    sequence: { useMaxWidth: false, wrap: true, width: 150, actorMargin: 40,
                messageFontSize: 14, noteFontSize: 14, actorFontSize: 14, mirrorActors: false },
    state: { useMaxWidth: false }, class: { useMaxWidth: false }
  });
  ```
- Render with `mermaid.render()` into your own container; never a bare `<pre class="mermaid">`.

## Size and zoom

- After render, read the `viewBox` and set the SVG `width` and `height` attributes to it; keep the numbers (`data-w`, `data-h`); `max-width: none`.
- **Show it at 100 % on load.** Never shrink a diagram to fit on load: a fitted wide diagram ends at 50 % and the text is unreadable. The frame is as tall as the diagram, up to about 70 % of the window, and scrolls.
- Zoom by changing the SVG `width` and `height` (vector, sharp at any zoom). Never a CSS `transform: scale`.
- Controls in the figure bar: − / percent / + / Fit / full screen (Escape closes). Ctrl or ⌘ + wheel zooms at the pointer; drag pans by scrolling the frame. Full screen opens at the fitted size but never below 100 %.
- Re-render every diagram when the theme changes, with colours from the page tokens.

## Drawing

- `flowchart TD` for more than four nodes; `LR` only for a short line of three or four.
- More than about 15 nodes: a small overview diagram plus detail cards.
- Label every arrow (`writes`, `polls every 30 s`); an unlabeled arrow says nothing.
- Two-line labels: use Mermaid Markdown strings (a backtick-quoted label with `**bold**` and a line break) or `<br/>`.
- One figure, one claim; the caption under the figure states it.
- Do not define a page-level `.node` class (Mermaid uses it).

## Robustness and access

- A failed diagram shows its error text in place, and a bar counts the failures. Never a silent blank.
- `role="img"` and an `aria-label` that says what the diagram shows, on the frame (not on the SVG, which re-renders).
- Set `body[data-done]` when all diagrams are drawn, so a headless check can wait for it.
