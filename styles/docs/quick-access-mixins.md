# Liftkit SCSS Quick Access: Mixins & Placeholders

A concise reference for developers: usage, syntax, and defaults for the most common mixins and placeholder selectors in the Liftkit SCSS framework.

---

## Spacing Mixins (`@include`)

| Mixin Syntax                          | Use Case / Description                    | Example Usage                         |
|---------------------------------------|-------------------------------------------|---------------------------------------|
| `@include margins.m-{dir}__{size}`    | Margin in direction (`top`, `bottom`, etc.)| `@include margins.m-bottom__md;`      |
| `@include margins.p-{dir}__{size}`    | Padding in direction                      | `@include margins.p-horizontal__sm;`  |
| `@include margins.adjust-to($lh)`     | Set spacing scale to given line-height     | `@include margins.adjust-to(1.6);`    |

- Directions: `top`, `right`, `bottom`, `left`, `vertical`, `horizontal`
- Sizes: `2xs`, `xs`, `sm`, `md`, `lg`, `xl`, `2xl`

---

## Typography Mixins

| Mixin Syntax                         | Use Case / Description                    | Example Usage                         |
|--------------------------------------|-------------------------------------------|---------------------------------------|
| `@include typography.declare(scale)` | Set font, line-height, spacing for scale  | `@include typography.declare('body');`|

- Scales: `display-1`, `display-2`, `title-a`, `body`, `caption`, etc.

---

## Color & Background Mixins

| Mixin Syntax                        | Use Case / Description                    | Example Usage                         |
|-------------------------------------|-------------------------------------------|---------------------------------------|
| `@include colors.bg__{role}`        | Set background color for theme role       | `@include colors.bg__surface;`        |
| `@include colors.fg__{role}`        | Set foreground/text color for theme role  | `@include colors.fg__on-surface;`     |

- Roles: `primary`, `surface`, `surface-variant`, `error`, etc.

---

## Shadow Mixins

| Mixin Syntax                        | Use Case / Description                    | Example Usage                         |
|-------------------------------------|-------------------------------------------|---------------------------------------|
| `@include shadows.shadow__{size}`   | Apply preset box-shadow                   | `@include shadows.shadow__md;`        |

- Sizes: `sm`, `md`, `lg`

---

## Sizing Mixins (`@include`)

| Mixin Syntax                             | Use Case / Description                    | Example Usage                            |
|-------------------------------------------|-------------------------------------------|------------------------------------------|
| `@include sizes.size(width, <size>)`      | Set fixed width                           | `@include sizes.size(width, sm);`       |
| `@include sizes.size(height, <size>)`     | Set fixed height                          | `@include sizes.size(height, lg);`      |

- Available sizes: `2xs`, `xs`, `sm`, `md`, `lg`, `xl`, `2xl`, `3xl`

---

## Flexbox & Layout Mixins

| Mixin Syntax                        | Use Case / Description                    | Example Usage                         |
|-------------------------------------|-------------------------------------------|---------------------------------------|
| `@include boxes.h-box__{size}`      | Horizontal flex container                 | `@include boxes.h-box__md;`           |
| `@include boxes.v-box__{size}`      | Vertical flex container                   | `@include boxes.v-box__sm;`           |
| `@include boxes.h-inline__{size}`   | Horizontal inline-flex container          | `@include boxes.h-inline__xs;`        |
| `@include boxes.v-inline__{size}`   | Vertical inline-flex container            | `@include boxes.v-inline__lg;`        |

---

## Placeholder Selectors (`%placeholder`)

| Placeholder Selector    | Use Case / Description                | Example Usage                      |
|------------------------|---------------------------------------|------------------------------------|
| `%card`                | Base card style (background, radius)  | `@extend %card;`                   |
| `%button`              | Base button style                     | `@extend %button;`                 |
| `%state`               | State overlay for interactive elems   | `@extend %state;`                  |

- Use `@extend %placeholder;` in your custom SCSS rules.

---

## Notes

- Mixins allow for argument customization and context-aware scaling.
- Placeholders are for structural reuse; they do not generate CSS unless extended.
- See partials in `styles/` for full argument lists and advanced usage.

---

For more, see [quick-access.md](./quick-access.md), [glossary.md](./glossary.md), and your SCSS partials.
