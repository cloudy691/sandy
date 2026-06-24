---
name: design-review
description: Comprehensive UI/UX design review for frontend code. Analyzes components for accessibility, responsiveness, visual hierarchy, color contrast, typography, spacing, and design system compliance. Identifies issues and suggests improvements with specific code changes.
---

# Frontend Design Review Skill

Review frontend code (HTML, CSS, JSX, Vue templates, Tailwind classes) for design quality, accessibility, and UX best practices.

## What to Review

When asked to review a design, check:

1. **Accessibility (WCAG 2.1 AA)**
   - Color contrast ratios (minimum 4.5:1 for normal text, 3:1 for large text)
   - Alt text on images
   - ARIA labels on interactive elements
   - Keyboard navigation support
   - Focus indicators
   - Semantic HTML elements

2. **Responsiveness**
   - Fluid typography and spacing
   - Breakpoint usage (mobile, tablet, desktop)
   - Flexible layouts (flexbox, grid)
   - Image/media scaling
   - Touch targets (minimum 44x44px)

3. **Visual Hierarchy**
   - Proper heading levels (h1-h6)
   - Size and weight differentiation
   - Alignment consistency
   - Spacing rhythm (8px grid preferred)
   - Whitespace usage

4. **Design System Compliance**
   - Reusable component patterns
   - Consistent naming conventions
   - Token usage (colors, spacing, fonts)
   - Shared utility classes over inline styles

5. **Performance**
   - Unused CSS removal
   - Image optimization hints
   - Critical CSS inlining opportunities
   - Animation performance (use transform/opacity)

6. **Modern Standards**
   - CSS custom properties over hardcoded values
   - Container queries when appropriate
   - Modern layout methods (grid, flex)
   - Reduced motion support

## How to Report Issues

For each issue found:
1. Quote the problematic code snippet
2. Explain what's wrong and why
3. Provide the corrected code
4. Classify severity (critical, warning, suggestion)
5. Reference the relevant guideline (WCAG, Material, Apple HIG, etc.)

## Output Format

```markdown
### Issue #[N]: [Short Description]
- **Severity:** [Critical | Warning | Suggestion]
- **Guideline:** [WCAG 2.1.4.6 / Best Practice]
- **Location:** [file:line or component name]

**Problem:**
```html/css/js
problematic code
```

**Fix:**
```html/css/js
corrected code
```

**Rationale:**
Explanation of why this matters.
```

## Priority Order

Critical issues first (accessibility failures, broken interactions), then warnings, then suggestions. End with a summary score and overall assessment.
