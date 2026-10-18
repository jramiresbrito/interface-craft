# Motion

From Emil Kowalski (emil-design-eng, animation-vocabulary; Sonner, Vaul, animations.dev), Rauno Freiberg ("Invisible Details of Interaction Design") and the Vercel Web Interface Guidelines. If the project's design system limits motion (for example "only colour and opacity, 150 ms or 300 ms"), that limit wins.

## Four questions before any animation

**1. How often is it seen?**

| Frequency | Decision |
|---|---|
| 100+ times a day (shortcuts, command palette) | No animation |
| Tens of times a day (hover, list navigation, tab switch) | None, or very small |
| Sometimes (modals, drawers, toasts) | A standard animation |
| Rarely (onboarding, success, celebration) | Delight is allowed |

Never animate a keyboard-initiated action. An indicator that feels nice on day one feels slow after a week.

**2. What is the purpose?** Spatial consistency, a state change, an explanation, feedback, or avoiding a jarring jump. "It looks cool" is not a purpose for anything seen often.

**3. Which easing?**

| Movement | Easing |
|---|---|
| Enter or exit | `ease-out` (default) |
| Move or morph on screen | `ease-in-out` |
| Hover, colour | `ease` |
| Constant (progress, marquee) | `linear` |

Never `ease-in` for UI. Stronger curves: ease-out `cubic-bezier(0.23, 1, 0.32, 1)`, ease-in-out `cubic-bezier(0.77, 0, 0.175, 1)`, iOS-like drawer `cubic-bezier(0.32, 0.72, 0, 1)`.

**4. How long?**

| Element | Duration |
|---|---|
| Button press | 100–160 ms |
| Tooltip, small popover | 125–200 ms |
| Dropdown, select | 150–250 ms |
| Modal, drawer | 200–500 ms |

UI motion stays under 300 ms. Faster feels better.

## Values that work

- **Press:** `transition: transform 160ms ease-out; :active { transform: scale(0.97) }`.
- **Enter:** from `scale(0.95); opacity: 0`, never `scale(0)`. Use `@starting-style` in CSS.
- **Popover:** `transform-origin` at the trigger; a modal stays centred.
- **Tooltip:** delay the first in a group, show the next ones at once; 125 ms `ease-out` from `scale(0.97); opacity: 0`.
- **Exit faster than enter.** Slow where the user decides (hold to delete, 2 s linear), fast where the system answers (release, 200 ms ease-out).
- **Lists:** stagger 30–80 ms; decoration only; never blocks a click.
- **Crossfade:** `filter: blur(2px)` during the swap hides the overlap; keep blur under 20 px.
- **Reveal:** `clip-path: inset(0 100% 0 0)` → `inset(0 0 0 0)`.

## Interruptible and physical

- CSS transitions for anything that can retrigger (a transition continues; keyframes restart from zero).
- Every animation can be interrupted by input. An animation you must wait out feels broken.
- Springs for drags: they keep velocity. `{ type: "spring", duration: 0.5, bounce: 0.2 }`; bounce 0.1–0.3 only for playful or drag-to-dismiss.
- Gestures: dismiss on velocity, not only distance; friction past a boundary instead of a hard stop; capture the pointer; ignore a second touch during a drag.
- A thrown object keeps the angle and speed of the throw; lighter objects bounce less.

## Performance

- Animate only `transform` and `opacity`. Never width, height, top, left, margin.
- Never `transition: all`.
- CSS for fixed animations, the Web Animations API for dynamic ones, a library last.
- Set `element.style.transform` directly instead of a CSS variable on a parent (that recalculates every child).
- SVG: animate a `<g>` with `transform-box: fill-box; transform-origin: center`.

## Accessibility

- `prefers-reduced-motion: reduce` means fewer and gentler animations, not zero: keep fades, remove movement.
- Hover effects only under `@media (hover: hover) and (pointer: fine)`.
- No autoplaying motion over 5 s without a pause.

## Words for asking (short vocabulary)

Use precise words to describe what you want: **fade, slide, scale in, pop, reveal** (enter and exit); **stagger, orchestration, delay, duration** (timing); **transform origin, origin-aware** (where it grows from); **crossfade, morph, shared element, layout animation, collapse** (between states); **press feedback, hold to confirm, swipe to dismiss, rubber-banding** (interaction); **ease-out, ease-in-out, spring, stiffness, damping, bounce, momentum, interruptible** (feel); **jank, dropped frame, compositing** (performance).

## Checking motion

Play it at 2–5× slower (DevTools Animations panel) and watch the start, the end, the origin, and whether opacity, transform and colour stay in step. Look again the next day.

| Problem | Fix |
|---|---|
| `transition: all` | Name the properties |
| Enter from `scale(0)` | `scale(0.95)` + `opacity: 0` |
| `ease-in` on UI | `ease-out` or a custom curve |
| Popover grows from its centre | Origin at the trigger |
| Animation on a keyboard action | Remove it |
| UI motion over 300 ms | 150–250 ms |
| Hover with no media query | `(hover: hover) and (pointer: fine)` |
| Keyframes on a rapid element | A transition |
| Enter and exit at the same speed | Exit faster |
| Everything appears at once | Stagger 30–80 ms |
