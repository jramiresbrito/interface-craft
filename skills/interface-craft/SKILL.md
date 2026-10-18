---
name: interface-craft
description: Use before you design, build, review or stress-test any user interface - a web page, an app screen, a documentation site, a dashboard, a component, a form, a chart, a diagram or an animation. One skill with three uses (build, review, break) that holds the rules of the best interface designers and engineers, so the result feels phenomenal, not just correct.
---

# Interface craft

A great interface feels right before the user can say why. That feeling comes from many small details that agree with each other. One wrong detail - a slow menu, a grey label you cannot read, a jump on load - is enough to lose it.

This skill distils the work of Emil Kowalski, Rauno Freiberg, the Vercel Web Interface Guidelines, Refactoring UI, the visual-explainer skill, the best documentation products, and a design system built for a real-time trading platform. Sources are in `references/sources.md`.

## Three uses

Pick the one that matches the request. There are no other commands.

| Use | When | What you deliver |
|---|---|---|
| **Build** (default) | "make", "design", "add", "redesign" a UI | The interface, plus the checklist of `references/review.md` filled in |
| **Review** | "review", "audit", "what is wrong with" a UI | A table of issues with Before, After and Why, worst first. Change nothing until asked |
| **Break** | "stress test", "break", "will this hold" | Worst-case data run through the UI and a report of what broke (`references/break.md`). Change nothing until asked |

## Which rules win

1. The words of the person who asked.
2. The project's own design system, if it has one. Read it completely first. Where it disagrees with this skill, follow the project and say so.
3. This skill.

## Build: the seven steps

1. **Know the reader and the job.** Who opens this, how often, and what must they do or decide in the first 5 seconds? A screen opened 50 times a day is designed differently from one opened once.
2. **One main idea per screen,** clear in the first viewport. Everything else is quieter.
3. **Structure before style:** the navigation levels, the order of sections, what is a list, a table, a card or a figure.
4. **Tokens:** 4 to 6 named colours with a light and a dark set, one font pair, a type scale, a spacing scale, radii, two shadow levels.
5. **Real content:** real names, the longest real value, the empty state and the error state. Never lorem ipsum.
6. **Interaction and motion last,** and only where they have a purpose.
7. **Look at it in a browser:** 390 and 1440 px, light and dark, the console, the keyboard. A page you did not see is not done.

## The twelve rules that matter most

1. **Hierarchy by weight and colour, not only size.** Three text colours (primary, secondary, tertiary), two or three weights. Quiet the neighbours instead of shouting the main item.
2. **Contrast you can read.** Body text 4.5:1 or more. A label that carries meaning (WHEN, THEN, a status) is never the lightest grey: give it full contrast or a tinted chip. Never meaning by colour alone.
3. **Quiet chrome, loud content.** Plain backgrounds, one accent colour, thin borders.
4. **A readable measure:** 60 to 75 characters a line, line height 1.5 to 1.7, balanced headings.
5. **Frequent actions are instant.** Command palette, shortcuts, tab switches: no animation.
6. **Motion is fast and has a purpose.** `ease-out` by default, under 300 ms, only `transform` and `opacity`, never `transition: all`, never `ease-in`, exits faster than entrances.
7. **Keyboard first:** everything reachable, with a visible `:focus-visible` ring.
8. **Targets of 24 px or more, 44 px on touch.** Anything that looks clickable is clickable.
9. **State lives in the URL:** tabs, filters, open panels, anchors.
10. **Design every state:** empty, one, many, very long, loading, error, stale, offline. No dead ends.
11. **Numbers line up:** tabular figures, one precision per column, a space before the unit.
12. **No generic look:** no purple gradient hero, no emoji section markers, no centred-everything, no grey-on-grey. It must not look like a default template.

## References

Open only what the task needs, and read the whole file you open.

| Topic | File |
|---|---|
| Colour, type, space, depth, dark mode, the generic look | `references/visual.md` |
| Keyboard, focus, targets, feedback, URL state, forms, phones | `references/interaction.md` |
| Any animation: when, easing, duration, values, vocabulary | `references/motion.md` |
| States, copy, numbers, tables, live data | `references/states-and-content.md` |
| Documentation sites and long reading pages | `references/docs-sites.md` |
| Diagrams (Mermaid) | `references/diagrams.md` |
| Worst-case data (the Break use) | `references/break.md` |
| The final checklist and the review format | `references/review.md` |
| Where each rule comes from | `references/sources.md` |
