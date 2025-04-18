# Design System - Quick Glossary & Use Cases

Focus: Quick lookup for applying styles.

## How do I...

**Apply Color?** (`appearance/_colors.scss`)

* **Text Color:**
    * `.text--primary`, `.text--secondary`, `.text--tertiary`, `.text--error`, etc.
    * `.text--surface` (for text on main background)
* **Background Color (with contrasting text):**
    * `.bg--primary`, `.bg--secondary`, `.bg--tertiary`, `.bg--error`, etc.
    * `.bg--surface` / `.bg--background` (main page/element background)
* **Container Background Color (text color *not* included):**
    * `.bg--primary-container`, `.bg--secondary-container`, etc.
* **Use Raw Color Variable (CSS):**
    * `color: var(--primary);`
    * `background-color: var(--surface);`

**Add Spacing (Margin/Padding)?** (`spacing/_margins.scss`)

* **Use SCSS Mixins (inside your selectors):**
    * Margin: `@include m-[top|right|bottom|left|vertical|horizontal]__[2xs|xs|sm|md|lg|xl|2xl];`
        * Example: `@include m-bottom__md;`
        * Example: `@include m-horizontal__lg;`
    * Padding: `@include p-[top|right|bottom|left|vertical|horizontal]__[2xs|xs|sm|md|lg|xl|2xl];`
        * Example: `@include p-top__sm;`
        * Example: `@include p-vertical__xl;`
* *(Note: These mixins rely on CSS variables `--xs` to `--2xl` which are set based on line-height in `_typography.scss`)*

**Create Layouts?**

* **Center Content (Max Width):** (`layout/_containers.scss`)
    * `<div class="container__md">...</div>` (Sizes: `xs`, `sm`, `md`, `lg`, `xl`)
* **Flexbox Row/Column (SCSS Mixins):** (`layout/_flex.scss`)
    * Row: `@include flex-row(sm);` (Optional gap: `xs` to `2xl`)
    * Column: `@include flex-col(md);` (Optional gap: `xs` to `2xl`)
    * Inline Row: `@include inline-flex-row();`
    * Inline Column: `@include inline-flex-col(xs);`
* **Grid Layout:** (`layout/_grids.scss`)
    * `<div class="grid grid--md col__4">...</div>`
        * `grid`: Base class
        * `grid--[xs|sm|md|lg|xl|2xl]`: Sets gap size
        * `col__[1-9]`: Sets number of columns
        * `row__[1-9]`: Sets number of rows (less common)
* **Stack Layers:** (`layout/_stacks.scss`)
    * `<div class="stack">`
        * `<div class="stack__layer">Bottom Layer</div>`
        * `<div class="stack__layer stack__layer--float stack__layer--above">Top Floating Layer</div>`
    * Modifiers: `--float`, `--above`, `--below`
* **Section Padding:** (`layout/_sections.scss`)
    * `<section class="section__lg">...</section>` (Sizes: `xs`, `sm`, `md`, `lg`, `xl`)

**Style Text?** (`typography/_typography.scss`)

* **Apply Typographic Scale:**
    * `.display-1`, `.display-2`
    * `.title-a`, `.title-b`, `.title-c`
    * `.heading`
    * `.subheading`
    * `.body` (Default paragraph style)
    * `.callout`
    * `.label`
    * `.caption`
    * `.overline`
* **Make Text Bolder:**
    * Append `--bold` to most scale classes (e.g., `.heading--bold`, `.label--bold`)

**Add Shadows?** (`appearance/_shadows.scss`)

* **Use SCSS Mixin/Placeholder (inside your selectors):**
    * `@include apply-shadow(md);` or `@extend %shadow__md;`
    * Sizes: `xs`, `sm`, `md`, `lg`, `xl`, `2xl`
* **Use Raw CSS Variable:**
    * `box-shadow: var(--shadow-lg);`

**Use Components?**

* **Button:** (`components/_buttons.scss`)
    * `<button class="button button--fill"> ... <span class="state"></span></button>`
    * Base: `.button`
    * Style: `.button--fill`, `.button--outline`
    * Icons: `.button--start-icon`, `.button--end-icon` (adjusts padding)
    * Size: `.button--large`
    * Content Wrapper: `<span class="button__content">...</span>`
    * Icon Wrapper: `<span class="button__icon">...</span>` (needs size mixin if SVG)
    * **Requires:** `<span class="state"></span>` inside for hover/focus/active effect.
* **Card:** (`components/_cards.scss`)
    * `<div class="card"> ... <span class="state"></span></div>`
    * Padding automatically scales based on largest text element inside (using `:has()`).
    * **OR** set padding explicitly: `.card--heading`, `.card--body`, etc.
    * **Requires:** `<span class="state"></span>` inside for hover/focus/active effect (optional).

**Apply Generic Size?** (`sizing/_scale.scss`)

* **Use SCSS Mixin (inside your selectors):**
    * `@include size(width, lg);`
    * `@include size(height, sm);`
    * `@include size(font-size, xl);`
    * Properties: Any CSS property accepting a size value.
    * Keys: `2xs`, `xs`, `sm`, `md`, `lg`, `xl`, `2xl`, `3xl` (maps to `--size-*` variables)

**Add Hover/Focus/Active State Effect?** (`state/_state-layers.scss`)

* Nest `<span class="state"></span>` as the *last* child inside the interactive element (button, card, link, etc.).
    ```html
    <a href="#" class="my-link">
      Link Text
      <span class="state"></span>
    </a>
    ```
