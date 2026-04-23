---
name: feature
description: Scaffold a new feature or page following the template's conventions (UIKit, TanStack Router, TanStack Query).
argument-hint: "<feature description>"
allowed-tools: Bash, Read, Write, Edit, Glob, Grep
---

Implement a new feature or page for this educational curriculum. $ARGUMENTS

## Before writing any code

1. Clarify scope if the description is ambiguous - ask the user rather than guess.
2. Read `CLAUDE.md` to confirm you have the conventions in mind.
3. If feature is related to curricula content, read `.claude/references/ilr.md` to apply the correct ILR design principles.
  - Determine the resource type: **Tutorial** (guided micro-lessons, 2-minute rule) or **Lab** (user stories, zero new concepts). This shapes the entire implementation.
5. Check `client/routes/` to understand the existing route structure before deciding where the new route lives.

## Implementation checklist

### Route
Create `client/routes/<name>.tsx` (or `<name>.$param.tsx` for parameterised routes):

```tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/name')({
  component: FeaturePage,
})

function FeaturePage() { ... }
```

Never create a `pages/` folder or use any router other than TanStack Router.

### Data fetching
If the feature loads external or async data, wrap it in `useQuery`. Never use raw `fetch` in a component body or `useEffect` for data loading:

```tsx
const { data, isPending } = useQuery({
  queryKey: ['feature-key'],
  queryFn: () => fetch('/data/feature.json').then(r => r.json()),
})
```

### Styling — UIKit first, Tailwind for layout
Apply fCC UIKit BEM classes for any component UIKit provides (buttons, badges, cards, typography, inputs):

```tsx
<button className="btn btn--cta">Continue</button>
<span className="badge badge--success">Complete</span>
```

Use Tailwind utilities only for layout, spacing, and anything UIKit does not cover. Do not apply shadcn primitives to anything UIKit already styles.

### Interactive primitives
For dialogs, dropdowns, comboboxes, popovers, or other stateful interactive elements UIKit doesn't cover, install the shadcn primitive first:

```bash
bunx --bun shadcn@latest add <component>
```

Then import from `@/components/ui/<component>`.

### TypeScript
Type all component props with `interface`. No `any`, no `@ts-ignore`.

### State and persistence
- Ephemeral interaction state: `useState`
- Cross-session persistence: `localStorage` (or a `useLocalStorage` hook)
- Never store progress in URL params

### ILR: Interactivity and evaluation
Apply the interactivity hierarchy - prefer in this order:
1. **Direct manipulation** (live editor, terminal emulator, logic board)
2. **Simulation** (adjustable variables with real-time visual feedback)
3. **Passive assessment** (multiple-choice, fill-in-the-blank — last resort only)

Every evaluation must include:
- A **learner-facing requirement** - plain sentence stating what the system checks
- An **assertion trace** - technical error detail for debugging
- **Pedagogical hints** - optional nudges after failed attempts, never revealing the answer

For **Tutorials**: each lesson must be completable in under 2 minutes and require at least one action. Use seeded state (pre-built scaffolding) so the learner focuses only on the target skill.

For **Labs**: express all requirements as User Stories. Introduce zero new concepts - only apply what prior tutorials taught.

## When done
Run `bun run build` to confirm there are no TypeScript or build errors before reporting the feature complete.
