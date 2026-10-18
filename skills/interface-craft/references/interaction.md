# Interaction

From the Vercel Web Interface Guidelines, Rauno Freiberg's "Invisible Details of Interaction Design", Emil Kowalski's mobile-native skill and a production trading-platform design system.

## Keyboard and focus

- Every flow works with the keyboard alone (WAI-ARIA Authoring Practices for menus, dialogs, tabs, listboxes).
- Every focusable element shows a ring on `:focus-visible` (not `:focus`); `:focus-within` for groups.
- A sticky header never covers the focused element or an anchored heading: set `scroll-margin-top`.
- A dialog traps focus, returns it to its trigger, and closes on Escape.
- Autofocus the single primary input on desktop; rarely on phones.
- Show shortcuts with the platform's symbols (Ctrl, ⌘) and make them work on other keyboard layouts.

## Targets and pointers

- Hit targets at least 24 × 24 px, 44 × 44 px on touch. If the visible part is smaller, enlarge the hit area.
- No dead zones: what looks interactive is interactive; a whole list row is the target.
- Links navigate (`<a>`), buttons act (`<button>`). Never a clickable `<div>`.
- Fitts's law: screen edges and corners are huge targets; put frequent targets near the pointer.
- During a drag, disable text selection and make the dragged element `inert`. Every gesture has a click and a keyboard alternative.

## Feedback and timing

- Respond at once: a press shows its state immediately, the result may follow.
- Loading: show a spinner or skeleton only after 150 to 300 ms, then keep it at least 300 to 500 ms so it never flashes. A skeleton has the exact shape of the content. A loading button keeps its label.
- Optimistic updates: show the result now; on failure roll back and say so, or offer Undo.
- Match the effort of an action to how reversible it is: reversible acts at once, irreversible gets a typed confirmation; the confirm button is never focused by default and never says only "Confirm".
- Light actions may fire during a gesture; destructive ones wait for release so the user can change their mind. Let the user peek and back out by reversing.

## Spatial consistency

- A thing opens from where it lives and closes back to it.
- What matters keeps its place on every screen (navigation, status, the danger switch). Layout may vary; meaning may not.
- The same gesture or key means the same thing everywhere.

## The URL is state

- Tabs, filters, sort, page, open panels and selections are in the URL: shareable, reload-safe, Back and Forward work.
- Restore scroll position on Back. Every heading and item has a stable, copyable anchor.

## Scrolling and overlays

- `overscroll-behavior: contain` on modals, drawers and inner scroll areas.
- Only useful scrollbars; test with scrollbars always visible.
- Hover styles only under `@media (hover: hover) and (pointer: fine)`.

## Forms

- Every control has a label; clicking it focuses the control. A checkbox and its label share one target.
- Do not block typing or pre-disable submit; show errors next to the field and focus the first one.
- Enter submits a single-field form; Ctrl or ⌘ + Enter submits a textarea.
- Correct `type`, `inputmode`, `autocomplete`, `enterkeyhint`; no spellcheck or autocorrect on codes and usernames; paste always allowed, also one-time codes.
- Placeholders show an example and end with `…`. Warn before leaving unsaved input.

## Phones (Emil Kowalski, mobile-native)

- Viewport: `width=device-width, initial-scale=1, viewport-fit=cover`. Never `user-scalable=no` or `maximum-scale=1`.
- `input, textarea, select { font-size: 16px }` or iOS zooms the page.
- App shells and drawers use `100dvh`; heroes `min-height: 100svh`; never `100vh` for a shell.
- `button, a, [role="button"] { touch-action: manipulation }`; `html { -webkit-tap-highlight-color: transparent; -webkit-text-size-adjust: 100% }`.
- Press feedback on `:active` (`scale(0.97)`, 100 to 160 ms `ease-out`).
- Safe areas: pad with `env(safe-area-inset-top)` and `env(safe-area-inset-bottom)` (with a `0px` fallback).
- `user-select: none` on controls only, never on `body`.
- Carousels: `touch-action: pan-y` or native `scroll-snap`.
- Verify on a real phone; code alone cannot prove it.

## Live screens

For any screen that changes by itself:

- One polite live region with summaries; only important events interrupt. Never a live region per cell.
- Update the changed rows, not the whole table.
- A stale value shows at lower contrast with its age.
- Never disturb an edit in progress with a live update.

## Implicit input

Use the context you already have (current project, last page, mode, time) instead of asking. Hide private content in screen shares and app switchers.
