---
description: Activated via /project:design. UI/component design specs, mobile review, interaction patterns. Replaces the ux-designer agent with a workflow-based skill.
---

# Design

Make products that people actually want to use — intuitive, beautiful, and fast.

## Anti-Rationalization

| Excuse | Why it fails |
|--------|-------------|
| "We'll fix the UX later" | Bad UX shipped is bad UX learned |
| "It works on desktop" | 60%+ of users are on mobile |
| "The engineer can figure out the layout" | Inconsistent UI erodes trust |

## Design Principles

1. **Mobile first** — design for 375px, scale up. Tap targets 44x44pt minimum.
2. **Clarity over cleverness** — one obvious next action per screen.
3. **Consistency builds trust** — reuse components, same interaction = same gesture.
4. **Speed is design** — skeleton screens, optimistic UI, animations under 300ms.
5. **Accessible by default** — WCAG AA contrast, focus states, no color-only signals.

## Process

### Step 1 — UX Review Checklist
Review the feature spec and answer:

**Layout & Structure**
- [ ] Primary action obvious at first glance
- [ ] Visual hierarchy guides the eye
- [ ] Consistent spacing (4px grid)
- [ ] Works at 375px, 768px, 1280px

**Mobile**
- [ ] Primary actions reachable with one thumb
- [ ] No horizontal scroll
- [ ] Correct input types (email, tel, number)
- [ ] Keyboard doesn't cover primary CTA

**States**
- [ ] Loading, empty, error, success — all defined
- [ ] Error messages tell users what to do

**Typography & Color**
- [ ] Type scale consistent with design system
- [ ] Body text >= 16px on mobile
- [ ] Contrast passes WCAG AA
- [ ] Dark mode considered

### Step 2 — Component Specs
For each new/modified component:

```markdown
## Component: [Name]

### Purpose
### Anatomy — elements, sizes, color tokens, spacing
### States — default, hover, pressed, disabled, loading, error
### Responsive behavior — mobile, tablet, desktop
### Accessibility — ARIA role, label, keyboard interaction
### Do / Don't
```

### Step 3 — Design Inspiration
Reference how leading products solve the same problem:

| Problem | Study |
|---------|-------|
| Onboarding | Duolingo, Headspace, Figma |
| Navigation | Instagram, Linear, Apple Settings |
| Forms | Stripe, Linear, Apple Pay |
| Loading | Airbnb, Vercel |
| Error handling | Stripe, GitHub, Linear |
| Data-heavy screens | Linear, Airtable, Retool |

### Step 4 — Handoff
Before implementation:
- [ ] Every screen state described
- [ ] Component inventory (reuse vs. new)
- [ ] Responsive notes per breakpoint
- [ ] Edge cases (long names, empty states, slow connections)
- [ ] Update `.claude/rules/ux-guidelines.md` if new patterns established
