# Dynamic Tailwind + JavaScript Patterns

## Table Of Contents

1. Build Sequence
2. Component Blueprint
3. JavaScript Interaction Recipes
4. Responsiveness And Accessibility
5. Delivery Checklist

## Build Sequence

1. Define page goal and top conversion action.
2. Sketch section order in plain HTML.
3. Apply layout and spacing with Tailwind utilities.
4. Layer visual treatment (color, typography, elevation, motion).
5. Add JavaScript interactivity using `data-*` hooks.
6. Verify keyboard flow, focus visibility, and mobile behavior.

## Component Blueprint

Use this structure for most sections:

```html
<section class="relative overflow-hidden py-16 md:py-24">
  <div class="mx-auto w-full max-w-6xl px-4 sm:px-6 lg:px-8">
    <header class="mb-8 md:mb-12">
      <p class="text-sm font-semibold uppercase tracking-[0.18em] text-slate-500">Label</p>
      <h2 class="mt-3 text-3xl font-black leading-tight text-slate-900 md:text-5xl">Headline</h2>
      <p class="mt-4 max-w-2xl text-base leading-relaxed text-slate-600 md:text-lg">
        Supporting copy that explains value and context.
      </p>
    </header>
    <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
      <!-- cards -->
    </div>
  </div>
</section>
```

## JavaScript Interaction Recipes

### Mobile Menu Toggle

```js
const menuButton = document.querySelector('[data-menu-button]');
const menuPanel = document.querySelector('[data-menu-panel]');

menuButton?.addEventListener('click', () => {
  const isOpen = menuPanel.classList.toggle('hidden') === false;
  menuButton.setAttribute('aria-expanded', String(isOpen));
});
```

### Tabs

```js
const tabButtons = document.querySelectorAll('[data-tab-button]');
const tabPanels = document.querySelectorAll('[data-tab-panel]');

tabButtons.forEach((button) => {
  button.addEventListener('click', () => {
    const tabId = button.dataset.tabButton;

    tabButtons.forEach((b) => b.classList.remove('bg-slate-900', 'text-white'));
    button.classList.add('bg-slate-900', 'text-white');

    tabPanels.forEach((panel) => {
      const active = panel.dataset.tabPanel === tabId;
      panel.classList.toggle('hidden', !active);
    });
  });
});
```

### Filterable Grid

```js
const filterButtons = document.querySelectorAll('[data-filter]');
const cards = document.querySelectorAll('[data-card]');

filterButtons.forEach((button) => {
  button.addEventListener('click', () => {
    const filter = button.dataset.filter;
    cards.forEach((card) => {
      const category = card.dataset.category;
      const visible = filter === 'all' || filter === category;
      card.classList.toggle('hidden', !visible);
    });
  });
});
```

### Accordion

```js
document.querySelectorAll('[data-accordion-trigger]').forEach((trigger) => {
  trigger.addEventListener('click', () => {
    const panel = document.getElementById(trigger.getAttribute('aria-controls'));
    const expanded = trigger.getAttribute('aria-expanded') === 'true';

    trigger.setAttribute('aria-expanded', String(!expanded));
    panel.classList.toggle('hidden', expanded);
  });
});
```

### Modal

```js
const modal = document.querySelector('[data-modal]');

document.querySelector('[data-modal-open]')?.addEventListener('click', () => {
  modal.classList.remove('hidden');
  modal.querySelector('[data-modal-close]')?.focus();
});

modal?.querySelector('[data-modal-close]')?.addEventListener('click', () => {
  modal.classList.add('hidden');
});
```

### Form Validation (Client-Side)

```js
const form = document.querySelector('[data-contact-form]');

form?.addEventListener('submit', (event) => {
  const email = form.querySelector('input[name="email"]');
  const error = form.querySelector('[data-email-error]');

  if (!email.value.includes('@')) {
    event.preventDefault();
    error.textContent = 'Enter a valid email address.';
    error.classList.remove('hidden');
    email.focus();
    return;
  }

  error.classList.add('hidden');
  error.textContent = '';
});
```

## Responsiveness And Accessibility

1. Use mobile-first classes and then scale with `sm:`, `md:`, `lg:`, `xl:`.
2. Keep touch targets large (`min-h-[44px]` and `px-4` minimum where possible).
3. Preserve visible focus rings on all controls.
4. Use descriptive `aria-label` and `aria-expanded` on toggles.
5. Respect reduced motion with conditional classes for heavy animation.

## Delivery Checklist

1. Confirm layout holds from narrow phones to wide desktop.
2. Confirm all interactive controls work by keyboard alone.
3. Confirm hidden states, empty states, and error states are rendered.
4. Confirm JavaScript selectors use stable `data-*` attributes.
5. Confirm final output is complete and runnable.
