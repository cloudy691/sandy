---
name: component-generator
description: Generates production-ready frontend components from descriptions. Supports React, Vue, Svelte, and plain HTML. Outputs accessible, responsive, well-structured code with CSS using Tailwind, CSS Modules, or vanilla CSS. Includes all necessary props/options documentation.
---

# Component Generator Skill

Generate clean, accessible, production-ready frontend components from natural language descriptions.

## Input Format

The user describes what they want, e.g.:
- "Create a primary button with hover states"
- "Build a card with image, title, description, and CTA"
- "Generate a navigation bar with dropdown menu"

## Output Components Include

1. **Component code** (chosen framework)
2. **Props/API documentation**
3. **Variants** (primary/secondary, size variations, dark/light mode)
4. **Accessibility features** built-in (ARIA, keyboard navigation, focus states)
5. **Responsive behavior** (mobile-first)

## Framework Detection

If the project has React/Vue/Svelte, use it. Otherwise, ask. Default to **React + Tailwind** if unspecified.

## Component Standards

### Structure
- Single responsibility principle
- Props with sensible defaults
- Forwarded refs where applicable
- Children composition over props drilling

### Styling
- Use design tokens (colors, spacing) — never hardcode hex values
- Mobile-first media queries
- Use CSS variables / Tailwind config for theming
- Dark mode support via prefers-color-scheme

### Accessibility
- Proper semantic HTML
- ARIA labels for icon-only buttons
- Keyboard support (Enter, Space, Escape, Arrow keys)
- Focus management
- Reduced motion media query

## Example Output

For "Create a primary button":

```tsx
import { forwardRef } from 'react'

type ButtonProps = {
  children: React.ReactNode
  onClick?: () => void
  variant?: 'primary' | 'secondary' | 'ghost'
  size?: 'sm' | 'md' | 'lg'
  disabled?: boolean
  type?: 'button' | 'submit' | 'reset'
  ariaLabel?: string
}

export const Button = forwardRef<HTMLButtonElement, ButtonProps>(
  ({ children, onClick, variant = 'primary', size = 'md', disabled, type = 'button', ariaLabel }, ref) => {
    const base = 'inline-flex items-center justify-center font-medium rounded-md transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-offset-2 disabled:opacity-50 disabled:cursor-not-allowed'

    const variants = {
      primary: 'bg-blue-600 text-white hover:bg-blue-700 focus-visible:ring-blue-500',
      secondary: 'bg-gray-100 text-gray-900 hover:bg-gray-200 focus-visible:ring-gray-500',
      ghost: 'text-gray-700 hover:bg-gray-100 focus-visible:ring-gray-500'
    }

    const sizes = {
      sm: 'text-sm px-3 py-1.5',
      md: 'text-base px-4 py-2',
      lg: 'text-lg px-6 py-3'
    }

    return (
      <button
        ref={ref}
        type={type}
        onClick={onClick}
        disabled={disabled}
        aria-label={ariaLabel}
        className={`${base} ${variants[variant]} ${sizes[size]}`}
      >
        {children}
      </button>
    )
  }
)

Button.displayName = 'Button'
```

## Design Decisions

Always explain design choices briefly:
- Why specific spacing values
- Why a particular color contrast
- Why a specific component structure
