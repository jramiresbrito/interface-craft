# Break: worst-case data

From Emil Kowalski's break-ui skill. Use it when asked to stress test a UI, and before you hand back any screen that shows data.

## The data

Every value is plausible, or the real limit from the schema or API. Random junk does not count. Spread the worst cases across rows so it still looks like real data.

- **Text:** very long names, one-letter names, multi-word names with suffixes, non-Latin scripts, diacritics, emoji, right-to-left text, long translated labels.
- **Identifiers:** long emails with no break points, long URLs, long unbroken strings (hashes, paths, keys).
- **Numbers:** 0, exactly 1 (plurals), very large values (separators), negative, null, NaN.
- **Collections:** empty, one item, the realistic upper bound (1,000+ rows if unpaginated).
- **Optional fields:** missing avatar, missing role, broken image URL.
- **Time:** just now, long ago, far future, unusual formats, time zones.
- **States:** every enum value, including ones the demo data never shows.

## Steps

1. **Map the surface:** every rendered value with its source, type, limit and whether it is optional. Note where the frontend and backend limits differ.
2. **Build the fixtures:** one worst case shaped like the demo data, plus empty, single and huge.
3. **Add a dev-only toggle** (Demo / Worst case / Empty / Huge) that swaps the data at the data boundary, never by editing markup or CSS. Keep the choice in the URL.
4. **Break it:** at the real width, at 320 px, at the widest layout, at 200 % zoom, in dark mode, in RTL if supported.
5. **Report and stop.** Fix nothing until asked.
6. **On request, fix,** then re-check every state including Demo; keep the fixture as a regression test.

## Report

1. **What broke** – a table ranked Broken, Ugly, Fragile: field, worst-case value, symptom, fix with the file.
2. **Decisions for you** – breaks with more than one valid fix, each with a recommendation.
3. **What held up** – the worst cases already handled.
4. **Close** – where the toggle is, its states, and "reply `fix all` or the numbers to fix".
