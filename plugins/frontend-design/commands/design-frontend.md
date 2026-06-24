---
name: design-frontend
description: Interactive design assistant command. Generate UI designs from text descriptions, review existing designs, create style guides, compare design alternatives, and output design tokens. Works with any frontend framework.
---

# /design-frontend Command

Interactive frontend design assistant. Use `/design-frontend` to generate UI designs, review existing code, or build design systems.

## Usage

### Generate UI from Description

```
/design-frontend [describe the component/page you want]
```

Examples:
- `/design-frontend login page with email and password fields`
- `/design-frontend dashboard with sidebar and data table`
- `/design-frontend pricing page with three tiers`

### Review Design

```
/design-frontend review [path to file or component]
```

Example:
- `/design-frontend review src/components/Card.tsx`
- `/design-frontend review this page's accessibility`

### Generate Design Tokens

```
/design-frontend tokens [framework]
```

Framework options: `tailwind` (default), `css-variables`, `styled-components`, `figma-tokens`

Example:
- `/design-frontend tokens tailwind`
- `/design-frontend tokens css-variables`

### Create Style Guide

```
/design-frontend styleguide [path]
```

Generates a comprehensive style guide from your component library.

## Design Principles

All generated designs follow:
- Mobile-first responsive design
- WCAG 2.1 AA accessibility standards
- Consistent spacing (4px/8px grid system)
- Semantic HTML
- Keyboard navigable
- Touch-friendly targets (44px minimum)
- Dark mode support via CSS variables
- Modern CSS (flexbox, grid, custom properties)

## Output

The command produces:
1. Complete component code in the detected or specified framework
2. Associated styles (Tailwind classes, CSS modules, or styled components)
3. Props/type definitions
4. Usage examples
5. Accessibility notes
6. Design tokens if applicable
