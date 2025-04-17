# Liftkit SCSS Quick Access

A concise reference for developers: syntax, use cases, and defaults for the main design system categories. Updated for BEM-style CSS custom properties and unified light/dark handling.

---

## Colors

| Class/Variable         | Use Case / Description                | Default (light / dark)                   |
|-----------------------|---------------------------------------|------------------------------------------|
| `.clr__primary`       | Main brand/action text                | `var(--clr__primary)`                    |
| `.clr__on-surface`    | Default text on backgrounds           | `var(--clr__on-surface)`                 |
| `.clr__on-surface-variant` | Subtle/secondary text           | `var(--clr__on-surface-variant)`         |
| `.clr__error`         | Error/alert text                      | `var(--clr__error)`                      |
| `var(--clr__*)`       | Use directly in custom CSS            | Defined in `styles/base/_globals.scss`   |

- All color variables use `light-dark()` for theme handling. No separate `.light`/`.dark` classes needed.

---

## Backgrounds

| Class                  | Use Case / Description                | Default (light / dark)                   |
|-----------------------|---------------------------------------|------------------------------------------|
| `.bg__surface`        | Main background for surfaces/cards     | `var(--clr__surface)`                    |
| `.bg__surface-variant`| Subtle alt backgrounds                | `var(--clr__surface-variant)`            |
| `.bg__primary`        | Brand-accented backgrounds            | `var(--clr__primary)`                    |
| `.bg__error`          | Error/alert backgrounds                | `var(--clr__error)`                      |

---

## Shadows

| Class                  | Use Case / Description                | Default                                 |
|-----------------------|---------------------------------------|------------------------------------------|
| `.shadow__sm`         | Small shadow (buttons, cards)         | `var(--clr__shadow)`                     |
| `.shadow__md`         | Medium shadow (modals, overlays)      | `var(--clr__shadow)`                     |
| `.shadow__lg`         | Large shadow (drawers, focus)         | `var(--clr__shadow)`                     |

- All shadows use `var(--clr__shadow)` for color.

---

## Typography

| Class/Element          | Use Case / Description                | Default                                 |
|-----------------------|---------------------------------------|------------------------------------------|
| `.rich-text h1, h2...`| Headings in rich text                 | `color: var(--clr__on-surface)`          |
| `.rich-text p, a`     | Paragraphs, links                     | `color: var(--clr__on-surface)`          |
| `.rich-text figcaption`| Figure captions                      | `color: var(--clr__on-surface-variant)`  |

---

## Spacing

| Class                  | Use Case / Description                | Default                                 |
|-----------------------|---------------------------------------|------------------------------------------|
| `.m-{size}`           | Margin (all sides)                    | e.g. `.m-2` for 0.5rem                   |
| `.mt-{size}`          | Margin top                            | e.g. `.mt-4` for 1rem                    |
| `.p-{size}`           | Padding (all sides)                   | e.g. `.p-2` for 0.5rem                   |
| `.pt-{size}`          | Padding top                           | e.g. `.pt-4` for 1rem                    |

- Sizing scale defined in spacing partials (e.g., `_margins.scss`).

---

## Usage Notes

- All color/background classes are theme-aware via CSS custom properties and `light-dark()`.
- No need for `.light` or `.dark` suffixes; use unified classes.
- For custom styles, use the CSS variables directly (e.g., `color: var(--clr__primary);`).
- See `styles/base/_globals.scss` for full variable list and defaults.

---

For more details, see the [glossary](./glossary.md) and [design-system.md](./design-system.md).
