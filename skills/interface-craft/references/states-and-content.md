# States, content, numbers and tables

From a production trading-platform design system, the Vercel Web Interface Guidelines and Refactoring UI.

## Every screen has all its states

The usual three (regular, empty, error) are not enough for anything with live data. Use seven, because "nothing happened today" and "the feed is dead" must look different:

1. **Regular** – the data is there and fresh.
2. **Empty** – says what is missing and what makes it appear. Real copy, no illustration.
3. **Error** – what failed, in plain words, and how to fix it.
4. **Stale** – old data: lower contrast and its age.
5. **Disconnected** – the live link is down: since when; the last values stay, marked.
6. **Degraded** – part of the data is missing or late: which part.
7. **Halted** – stopped on purpose (a pause, a kill switch): who and why.

Also: one item, many items, the longest real value, an unbroken word (path, hash, URL), and loading. No dead ends: every state offers the next step.

## Copy

- Write each string where you design the screen. No placeholder text.
- Name things by what the reader knows, not by internal structure.
- Controls say exactly what happens ("Save the limit", not "Continue").
- Error messages say how to fix the problem.
- Numerals for counts ("8 runs"); a space before units ("10 MB").
- Labels are a last resort: a value whose format speaks for itself needs none.
- Never meaning by colour alone; icons get accessible names.
- `<title>` matches the page and its state.

## Numbers

- `font-variant-numeric: tabular-nums` (or mono) wherever numbers are compared or update.
- One precision per column, not per value. Right-align; align decimal points.
- Locale-aware dates, times and numbers; show the time zone when it matters.
- A changing number is highlighted with a brief colour tint, never with movement.

## Tables

- Fixed column widths; never let content widths make the columns jump.
- No zebra stripes when rows are tinted for state; no shadow on a row.
- A sticky header never covers the focused row.
- Long cell text wraps or truncates with the full value on hover and focus; hashes and paths break anywhere.
- Wide tables scroll in their own container, never the page.

## Two texts side by side

A pair of texts in a row needs a minimum width that comes from the texts, not from a fixed column count or a multiple of the font size (character widths differ by font and by value). A layout that fits at 390 and 1440 px can still break between them: check the widths in between.

## Danger and mode

When the system has modes with different stakes (test and live, draft and published), the current mode is always visible and never in a badge that scrolls away. Match the effort of an action to how reversible it is.
