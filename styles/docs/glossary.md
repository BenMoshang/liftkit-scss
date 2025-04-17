Okay, here are the documentation and glossary formatted in Markdown:

## LiftKit v1.3.0 Documentation

### 1. Overview

LiftKit is described as a lightweight SCSS framework aimed at creating clean, minimalist designs. It utilizes a modular structure, leveraging Sass's `@use` rule to organize styles into different categories like base, layout, spacing, typography, appearance, sizing, interactivity, and components. The framework heavily relies on the golden ratio (`ϕ`) for defining its scaling, sizing, and spacing system. It also incorporates a theming system with light and dark modes based on Material Design color principles.

**License:** GNU Affero General Public License v3 (AGPL-3.0).

### 2. Core Concepts

* **Golden Ratio Scaling:** Many dimensions (font sizes, spacing units, component sizes) are derived from the golden ratio (`$SCALE = 1.618...`) and its powers, aiming for harmonious proportions.
* **Modular Structure:** Styles are broken down into logical modules (e.g., `_globals.scss`, `_typography.scss`, `_buttons.scss`) imported into the main `main.scss` file.
* **CSS Variables:** Extensive use of CSS custom properties (variables) for theming (colors) and dynamic spacing based on context (e.g., line-height in `_margins.scss`, scale in `_cards.scss`).
* **Utility Mixins/Classes:** Provides reusable mixins (primarily) and some utility classes for common styling tasks like applying margins/padding, setting dimensions, creating layouts (flexbox boxes, grids, stacks), and applying colors or shadows.
* **Theming:** Includes predefined light and dark color palettes accessible via CSS variables (e.g., `--primary`, `--surface`, `--on-background`). The dark theme is applied automatically based on user preference (`prefers-color-scheme: dark`). Mixins like `bg__primary` or `fg__on-surface` simplify applying theme colors.

### 3. File Breakdown & Use Cases

* **`main.scss`**
  * **Purpose:** The main entry point that imports all other partials. Contains the framework version debug message (`LiftKit-v1.3.0`).
  * **Use Case:** This is the file you would typically compile to produce the final CSS output for your project.

* **`base/_globals.scss`**
  * **Purpose:** Defines fundamental constants, primarily the golden ratio (`$SCALE`) and derived values (`$MAJOR`, `$MINOR`, etc.), size variables (`$SIZE-MD`, `$SIZE-LG`, etc.), and a precision rounding function (`round-to`).
  * **Use Case:** These variables are used throughout the framework by other modules to ensure consistent scaling and sizing. You might adjust `$SCALE` or `$PRECISION` for customization, though it would have wide-ranging effects.

* **`base/_resets.scss`**
  * **Purpose:** Applies baseline resets to common HTML elements for cross-browser consistency (e.g., sets `box-sizing: border-box`, removes default margins/paddings, styles links). Applies default background and text color from the theme to the `body`.
  * **Use Case:** Included automatically to provide a consistent starting point, reducing browser default style interference.

* **`layout/_containers.scss`**
  * **Purpose:** Defines centered container classes (`.container__xs` to `.container__xl`) with different `max-width` values based on a base width (`$_WIDTH: 1000px`) and golden ratio scaling.
  * **Use Case:** Wrap main page content or sections within these classes to center them horizontally with controlled maximum widths. Example: `<div class="container__md">... page content ...</div>`.

* **`layout/_grids.scss`**
  * **Purpose:** Provides classes for creating CSS grid layouts. `.grid` sets up the display, while modifiers like `--sm`, `--md`, etc., control the `gap` size. `.col__#` and `.row__#` modifiers set the number of columns or rows.
  * **Use Case:** Create grid structures for arranging content. Example: `<div class="grid grid--md col__3"> <div>Item 1</div> <div>Item 2</div> <div>Item 3</div> </div>`.

* **`layout/_sections.scss`**
  * **Purpose:** Defines classes for adding vertical and horizontal padding to sections (`.section__xs` to `.section__xl`). Padding values are responsive, adjusting on smaller screens.
  * **Use Case:** Apply these classes to `<section>` or `<div>` elements to give them consistent spacing. Example: `<section class="section__md">...</section>`.

* **`layout/_stacks.scss`**
  * **Purpose:** Creates layered layouts using CSS Grid (`.stack`). Child elements with `.stack__layer` are placed in the same grid cell. Modifiers (`--float`, `--above`, `--below`) control positioning and z-index.
  * **Use Case:** Useful for overlaying elements, like placing text over an image background. Example: `<div class="stack"> <img src="..." class="stack__layer"> <div class="stack__layer stack__layer--float">Overlay Text</div> </div>`.

* **`spacing/_margins.scss`**
  * **Purpose:** Provides a comprehensive set of mixins for applying margin (`m-`) and padding (`p-`) in different directions (top, right, bottom, left, vertical, horizontal) and sizes (`2xs` to `2xl`). The `adjust-to` mixin dynamically calculates spacing variables based on line height.
  * **Use Case:** Apply spacing within your custom CSS rules using `@include`. Example: `.my-component { @include margins.m-bottom__md; @include margins.p-vertical__sm; }`. The variables (`--xs`, `--sm`, etc.) are defined based on the context's line-height, often set by typography classes.

* **`typography/_typography.scss`**
  * **Purpose:** Defines a detailed typographic scale (from `.display-1` down to `.overline`) with specific font sizes, weights, line heights, and letter spacing. Sets root font styles and provides classes for applying each type scale style. Includes responsive adjustments for larger styles.
  * **Use Case:** Apply typography classes directly to HTML elements. Example: `<h1 class="display-1">Title</h1> <p class="body">Paragraph text.</p> <span class="label label--bold">Important Label</span>`. The `declare` mixin can be used in custom components to inherit typographic properties.

* **`appearance/_background-colors.scss`**
  * **Purpose:** Defines light and dark color themes using CSS variables (e.g., `--primary`, `--on-primary`, `--surface`). Provides numerous mixins for applying foreground (`fg__*`) and background (`bg__*`) styles according to the theme roles.
  * **Use Case:** Apply theme colors using mixins in custom SCSS rules (e.g., `.my-alert { @include colors.bg__error-container; }`) or directly use the CSS variables (e.g., `border: 1px solid var(--outline);`). The theme switches automatically with OS preference, but can be overridden.

* **`appearance/_shadows.scss`**
  * **Purpose:** Defines mixins for applying preset box-shadow styles (`shadow__xs` to `shadow__2xl`).
  * **Use Case:** Add elevation and depth to elements using `@include`. Example: `.my-popup { @include shadows.shadow__lg; }`.

* **`sizing/_scale.scss`**
  * **Purpose:** Provides mixins for setting fixed widths (`w__*`) and heights (`h__*`) based on the global size variables defined in `_globals.scss`.
  * **Use Case:** Apply fixed dimensions to elements where needed. Example: `.avatar { @include sizes.w__sm; @include sizes.h__sm; border-radius: 50%; }`.

* **`interactivity/_state-layers.scss`**
  * **Purpose:** Defines a `.state` class intended to be nested within interactive elements. It provides a subtle background overlay on `:hover`, `:active`, and `:focus-visible` states.
  * **Use Case:** Include `<span class="state"></span>` inside buttons or other interactive components to get visual feedback on interaction. Example: `<button class="button">Action <span class="state"></span></button>`.

* **`components/_boxes.scss`**
  * **Purpose:** Provides mixins for creating flexbox layouts (horizontal/vertical, block/inline) with specified gap sizes (`__xs` to `__2xl`).
  * **Use Case:** Quickly apply flexbox layouts with consistent spacing within custom components. Example: `.icon-text { @include boxes.h-inline__sm; align-items: center; }`.

* **`components/_buttons.scss`**
  * **Purpose:** Styles `.button` elements. Provides modifiers for appearance (`--fill`, `--outline`), icons (`--start-icon`, `--end-icon`), and size (`--large`). Requires a `.button__content` wrapper for icon layouts and potentially a `.state` element for interaction feedback.
  * **Use Case:** Create styled buttons. Example: `<button class="button button--fill"> <span class="button__content"> <svg class="button__icon">...</svg> <span>Submit</span> </span> <span class="state"></span> </button>`. `<a href="#" class="button button--outline">Learn More <span class="state"></span></a>`.

* **`components/_cards.scss`**
  * **Purpose:** Styles `.card` elements with themed background, padding, and border-radius. Padding is dynamically adjusted based on the largest typography scale used within the card (or explicitly set via modifiers like `--title-a`).
  * **Use Case:** Group related content within a card. Example: `<div class="card card--body"> <h3 class="heading">Card Title</h3> <p class="body">Card content goes here.</p> <a href="#" class="button">Action</a> </div>`.

---

## LiftKit Syntax Glossary

### Layout

* **`.container__<size>`** (e.g., `.container__md`, `.container__lg`)
  * **Purpose:** Creates a centered container with a specific `max-width`. Sizes range from `xs` to `xl`.
  * **Use Case (HTML):**

        ```html
        <div class="container__lg"> ... content ... </div>
        ```

* **`.grid`**
  * **Purpose:** Base class to establish a CSS grid container. Defaults to 2 columns.
  * **Use Case (HTML):**

        ```html
        <div class="grid"> ... grid items ... </div>
        ```

* **`.grid--<size>`** (e.g., `.grid--sm`, `.grid--lg`)
  * **Purpose:** Modifier for `.grid` to set the `gap` between grid items. Sizes range from `xs` to `2xl`.
  * **Use Case (HTML):**

        ```html
        <div class="grid grid--md"> ... grid items ... </div>
        ```

* **`.col__<n>` / `.row__<n>`** (e.g., `.col__3`, `.row__2`)
  * **Purpose:** Modifier for `.grid` to set the number of columns (`col__n`) or rows (`row__n`). `n` can be 1 through 9.
  * **Use Case (HTML):**

        ```html
        <div class="grid grid--md col__4"> ... 4 columns ... </div>
        ```

* **`.section__<size>`** (e.g., `.section__xs`, `.section__md`)
  * **Purpose:** Applies consistent vertical and horizontal padding to a section. Padding is responsive. Sizes range from `xs` to `xl`.
  * **Use Case (HTML):**

        ```html
        <section class="section__lg"> ... section content ... </section>
        ```

* **`.stack`**
  * **Purpose:** Creates a container where child `.stack__layer` elements are layered on top of each other using CSS grid.
  * **Use Case (HTML):**

        ```html
        <div class="stack">
          <img class="stack__layer" src="..." alt="...">
          <div class="stack__layer">Overlay</div>
        </div>
        ```

* **`.stack__layer`**
  * **Purpose:** Denotes a child element within a `.stack` container.
  * **Use Case (HTML):** See `.stack`.

* **`.stack__layer--float`, `--above`, `--below`**
  * **Purpose:** Modifiers for `.stack__layer` to control positioning (`--float` uses `position: absolute`) and `z-index` (`--above`, `--below`).
  * **Use Case (HTML):**

        ```html
        <div class="stack">
           <img class="stack__layer" src="..." alt="...">
           <div class="stack__layer stack__layer--float stack__layer--above">Absolute Overlay</div>
         </div>
        ```

### Typography

* **`.display-1`, `.display-2`, `.title-a`, ..., `.overline`**
  * **Purpose:** Applies specific typographic styles (font size, weight, line height, letter spacing) defined in the type scale.
  * **Use Case (HTML):**

        ```html
        <h1 class="display-1">Page Title</h1>
        <p class="body">Text...</p>
        ```

* **`<type-class>--bold`** (e.g., `.label--bold`)
  * **Purpose:** Applies the bold font-weight variant for the specified type class (if defined).
  * **Use Case (HTML):**

        ```html
        <span class="label label--bold">Important</span>
        ```

* **`@include typography.declare(<scale>)`**
  * **Purpose:** (SCSS Mixin) Applies the font size, line height, letter spacing, and default weight for a given type scale (e.g., 'body', 'heading') within a custom rule. Also adjusts spacing variables using `margins.adjust-to`.
  * **Use Case (SCSS):**

        ```scss
        .custom-text {
          @include typography.declare("caption");
        }
        ```

* **`@include margins.adjust-to(<line-height>)`**
  * **Purpose:** (SCSS Mixin) Sets CSS variables (`--xs`, `--sm`, etc.) used by margin/padding mixins based on the provided unitless line-height. Automatically called by `@include typography.declare`.
  * **Use Case (SCSS):**

        ```scss
        .special-area {
          line-height: 1.8;
          @include margins.adjust-to(1.8); // Usually handled by typography classes
        }
        ```

### Spacing

* **`@include margins.m-<dir>__<size>`** (e.g., `@include margins.m-top__md`, `@include margins.m-horizontal__sm`)
  * **Purpose:** (SCSS Mixin) Applies `margin` to the specified direction(s) (`top`, `right`, `bottom`, `left`, `vertical`, `horizontal`) using pre-calculated sizes (`2xs` to `2xl`) stored in CSS variables.
  * **Use Case (SCSS):**

        ```scss
        .my-element {
          @include margins.m-bottom__lg;
        }
        ```

* **`@include margins.p-<dir>__<size>`** (e.g., `@include margins.p-vertical__xs`, `@include margins.p-left__xl`)
  * **Purpose:** (SCSS Mixin) Applies `padding` similar to the margin mixins.
  * **Use Case (SCSS):**

        ```scss
        .my-container {
          @include margins.p-vertical__md;
          @include margins.p-horizontal__lg;
        }
        ```

### Appearance

* **`@include colors.bg__<role>`** (e.g., `@include colors.bg__primary`, `@include colors.bg__surface-container`)
  * **Purpose:** (SCSS Mixin) Applies the background color for the specified theme role and sets the appropriate foreground color (`color`) for contrast.
  * **Use Case (SCSS):**

        ```scss
        .themed-box {
          @include colors.bg__secondary-container;
        }
        ```

* **`@include colors.fg__<role>`** (e.g., `@include colors.fg__on-surface`, `@include colors.fg__error`)
  * **Purpose:** (SCSS Mixin) Applies the `color` (text color) for the specified theme role.
  * **Use Case (SCSS):**

        ```scss
        .error-message {
          @include colors.fg__error;
        }
        ```

* **`var(--<color-role>)`** (e.g., `var(--primary)`, `var(--outline)`)
  * **Purpose:** (CSS Variable) Direct access to the theme color values.
  * **Use Case (CSS/SCSS):**

        ```css
        border: 1px solid var(--outline-variant);
        ```

* **`@include shadows.shadow__<size>`** (e.g., `@include shadows.shadow__sm`, `@include shadows.shadow__xl`)
  * **Purpose:** (SCSS Mixin) Applies a predefined `box-shadow` style. Sizes range from `xs` to `2xl`.
  * **Use Case (SCSS):**

        ```scss
        .popup {
          @include shadows.shadow__lg;
        }
        ```

### Sizing

* **`@include sizes.size(width, <size>)` / `@include sizes.size(height, <size>)`** (e.g., `@include sizes.size(width, md)`, `@include sizes.size(height, sm)`)
  * **Purpose:** (SCSS Mixin) Applies a fixed `width` or `height` based on the global size scale. Sizes range from `2xs` to `3xl`.
  * **Use Case (SCSS):**

        ```scss
        .avatar-icon {
          @include sizes.size(width, sm);
          @include sizes.size(height, sm);
        }
        ```

### Components

* **`@include boxes.<type>__<size>`** (e.g., `@include boxes.h-box__md`, `@include boxes.v-inline__sm`)
  * **Purpose:** (SCSS Mixin) Creates a flexbox container (`h-box`, `v-box`, `h-inline`, `v-inline`) with a specified `gap`. Sizes range from `xs` to `2xl`.
  * **Use Case (SCSS):**

        ```scss
        .button-group {
          @include boxes.h-inline__xs;
        }
        ```

* **`.button`**
  * **Purpose:** Base class for button styling.
  * **Use Case (HTML):**

        ```html
        <button class="button">...</button>
        <a href="#" class="button">...</a>
        ```

* **`.button--fill`, `--outline`, `--large`**
  * **Purpose:** Modifier classes for button appearance (`fill`, `outline`) and size (`large`).
  * **Use Case (HTML):**

        ```html
        <button class="button button--fill button--large">...</button>
        ```

* **`.button--start-icon`, `--end-icon`**
  * **Purpose:** Modifier classes to adjust padding when an icon is present at the start or end.
  * **Use Case (HTML):** `<button class="button button--start-icon">...</button>` (Used with `.button__content` and `.button__icon`).

* **`.button__content`**
  * **Purpose:** Internal wrapper for button text and icons, applies flex layout.
  * **Use Case (HTML):** `<button class="button"><span class="button__content">...</span></button>`

* **`.button__icon`**
  * **Purpose:** Class for styling icons within a button, typically an `svg` or `i` tag. Sets a default size.
  * **Use Case (HTML):**

        ```html
        <button class="button button--start-icon">
          <span class="button__content">
             <svg class="button__icon">...</svg> Text
           </span>
         </button>
        ```

* **`.card`**
  * **Purpose:** Base class for card components. Applies background, padding, border-radius, and overflow hidden. Padding dynamically adjusts based on content.
  * **Use Case (HTML):**

        ```html
        <div class="card"> ... card content ... </div>
        ```

* **`.card--<type-scale>`** (e.g., `.card--body`, `.card--heading`)
  * **Purpose:** Modifier for `.card` to explicitly set the scale used for calculating padding, overriding the automatic detection.
  * **Use Case (HTML):**

        ```html
        <div class="card card--title-c"> ... content primarily using title-c style ... </div>
        ```

### Interactivity

* **`.state`**
  * **Purpose:** An empty element placed inside an interactive component (like `.button`) to provide visual feedback (a semi-transparent overlay) on `:hover`, `:active`, and `:focus-visible` states.
  * **Use Case (HTML):**

        ```html
        <button class="button">Click Me <span class="state"></span></button>
        ```
