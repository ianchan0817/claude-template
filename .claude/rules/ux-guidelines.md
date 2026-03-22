---
description: UX design guidelines — maintained by the UX Designer. Covers layout, mobile, typography, color, spacing, interaction patterns, and component conventions for this project.
---

# UX Guidelines

Maintained by `ux-designer`. Updated after each sprint when new patterns are established.

## Spacing Scale (4px base grid)

| Token | Value | Usage |
|-------|-------|-------|
| space-1 | 4px | Tight internal padding |
| space-2 | 8px | Icon gaps, inline spacing |
| space-3 | 12px | Compact component padding |
| space-4 | 16px | Standard padding |
| space-6 | 24px | Section gaps |
| space-8 | 32px | Large section separation |
| space-12 | 48px | Page-level padding |

## Typography Scale

| Token | Size | Weight | Usage |
|-------|------|--------|-------|
| display | 32px+ | 700 | Hero headings |
| h1 | 28px | 700 | Page titles |
| h2 | 22px | 600 | Section headings |
| h3 | 18px | 600 | Card headings |
| body | 16px | 400 | Default body text |
| small | 14px | 400 | Captions, labels |
| micro | 12px | 400 | Timestamps, metadata only |

Never use anything below 12px. Never use micro for primary content.

## Color Usage

- **Primary** — main actions, links, active states
- **Destructive** — delete, remove, irreversible actions (always confirm)
- **Success** — confirmations, completed states
- **Warning** — non-blocking issues requiring attention
- **Muted** — disabled states, secondary text
- Color must never be the only signal — pair with icon or label

## Mobile Rules

- All tap targets minimum 44×44pt
- Primary CTA always visible without scrolling on mobile
- No horizontal overflow
- Forms: correct input types (`email`, `tel`, `number`, `search`)
- Bottom sheet > modal for mobile confirmations

## Interaction Patterns

- Transitions: 200–300ms, ease-out
- Response feedback (tap, toggle): 100–150ms
- Never animate purely functional actions
- Skeleton screens for content loads > 300ms
- Optimistic UI for: likes, saves, toggles, reactions

## Component Conventions

<!-- Populated as components are designed. Example: -->
<!-- ### Button -->
<!-- - Primary: filled, full-width on mobile -->
<!-- - Secondary: outlined -->
<!-- - Destructive: red variant, requires confirmation dialog -->
