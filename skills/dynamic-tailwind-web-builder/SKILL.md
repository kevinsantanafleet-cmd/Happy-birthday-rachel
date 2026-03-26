---
name: dynamic-tailwind-web-builder
description: Build dynamic, responsive websites using HTML, Tailwind CSS, and JavaScript. Use when Codex needs to create or refactor landing pages, product pages, dashboards, portfolios, or interactive UI components with client-side behavior such as tabs, filters, modals, accordions, form validation, and stateful interactions.
---

# Dynamic Tailwind Web Builder

## Overview

Build polished, responsive websites with semantic HTML, utility-first Tailwind styling, and framework-free JavaScript behavior. Deliver production-ready layouts that feel intentional, accessible, and interactive on both mobile and desktop.

## Workflow

1. Clarify the page goal, audience, and required interactions.
2. Choose an architecture:
- Use a single `index.html` file for small pages.
- Use `index.html` plus `main.js` for richer interactions.
- Add `styles.css` only when Tailwind utilities alone become noisy.
3. Build semantic HTML structure before adding visual detail.
4. Style with Tailwind using consistent spacing, typography, and color tokens.
5. Add JavaScript for behavior and state, then refine accessibility and motion.
6. Verify responsive behavior, keyboard support, and empty/error states.

## Layout And Visual Direction

1. Start with a clear visual concept before coding details.
2. Define reusable tokens in Tailwind classes (spacing, radius, text scale, shadows).
3. Use expressive typography choices and strong hierarchy.
4. Avoid flat or generic styling; add gradients, subtle textures, or layered surfaces when appropriate.
5. Keep contrast accessible and preserve legibility on all breakpoints.

## Dynamic JavaScript Patterns

1. Use `data-*` attributes to bind behavior to elements.
2. Keep state in small plain objects or arrays.
3. Prefer event delegation for repeated or dynamic elements.
4. Handle loading, empty, and error states explicitly.
5. Keep animation purposeful and lightweight.
6. Favor progressive enhancement so core content still works without JavaScript.

## Accessibility And Quality Checks

1. Use semantic tags (`header`, `main`, `section`, `nav`, `footer`) and logical heading order.
2. Ensure interactive controls are keyboard reachable and visibly focusable.
3. Add `aria-expanded`, `aria-controls`, and live-region text where needed.
4. Respect reduced motion preferences for animated UI.
5. Test on narrow and wide viewports before finalizing output.

## Output Requirements

1. Return complete runnable code, not fragments, unless the user requests partial edits.
2. Keep HTML, Tailwind classes, and JavaScript organized and easy to scan.
3. Explain where dynamic behavior lives and how to extend it.
4. Include brief test instructions for interaction-heavy pages.
5. If a request is ambiguous, choose sensible defaults and state assumptions after implementation.

## References

Use [references/patterns.md](references/patterns.md) for ready-to-adapt Tailwind component structures and JavaScript interaction recipes.
