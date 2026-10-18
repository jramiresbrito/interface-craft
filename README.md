# interface-craft

One agent skill for building phenomenal user interfaces.

It gathers what the best interface designers and engineers teach – Emil Kowalski, Rauno Freiberg, the Vercel Web Interface Guidelines, Refactoring UI, the best documentation products – plus rules learned the hard way on a real-time trading platform, into one skill that an AI agent (Claude Code and others) loads before it designs, builds or reviews a UI.

## Install

```bash
npx skills add jramiresbrito/interface-craft
```

Or copy `skills/interface-craft/` into your project's `.claude/skills/` (or `~/.claude/skills/` for every project).

## Use

There are no commands to learn. Ask for UI work as usual; the skill picks one of three uses:

| Use | Say | You get |
|---|---|---|
| **Build** | "build", "design", "redesign" a page or component | The interface, checked against a short checklist |
| **Review** | "review", "audit" a UI | Issues worst first, as Before / After / Why. Nothing changes until you say so |
| **Break** | "stress test", "break" a UI | Worst-case data through the UI and a report of what broke |

Your project's own design system always wins over the skill.

## What is inside

| File | About |
|---|---|
| `SKILL.md` | The three uses, the seven build steps, the twelve rules that matter most |
| `references/visual.md` | Colour, type, space, depth, dark mode, how not to look generic |
| `references/interaction.md` | Keyboard, focus, targets, feedback, URL state, forms, phones, live screens |
| `references/motion.md` | When to animate, easing, durations, exact values, a short vocabulary |
| `references/states-and-content.md` | Seven screen states, copy, numbers, tables |
| `references/docs-sites.md` | Documentation sites and long reading pages |
| `references/diagrams.md` | Mermaid diagrams that stay sharp and readable |
| `references/break.md` | Worst-case data and the stress-test report |
| `references/review.md` | The final checklist and the review format |
| `references/sources.md` | Every source, with links |

## Credits

The rules are restated in our own words from the sources in `references/sources.md`. Emil Kowalski's skills and the Vercel Web Interface Guidelines are MIT-licensed; go read them – they are excellent.

## Licence

MIT
