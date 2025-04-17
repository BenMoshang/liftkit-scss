**LiftKit v1.3.0 Documentation**

**1. Overview**

LiftKit is a lightweight SCSS framework for minimalist, harmonious design. It uses a modular Sass structure, golden ratio-based scaling, and a modern theming system built on CSS custom properties (`--clr__*`). Theming leverages the `light-dark()` function for automatic light/dark adaptation, eliminating the need for separate mode classes.

**License:** GNU Affero General Public License v3 (AGPL-3.0).

**2. Core Concepts**

* **Golden Ratio Scaling:** All major dimensions use the golden ratio (`$SCALE = 1.618...`) for visual harmony.
* **Modular Structure:** Styles are organized into logical modules (e.g., `_globals.scss`, `_typography.scss`, `_buttons.scss`) and imported into `main.scss`.
* **CSS Custom Properties:** The framework uses BEM-style CSS variables (e.g., `--clr__primary`, `--clr__on-surface`) for all theming and color roles. These are defined in `base/_globals.scss` and are accessible throughout.
* **Utility Mixins/Classes:** Provides reusable mixins and utility classes for spacing, layout, color, and shadows.
* **Theming:** Theme colors are handled via CSS custom properties and the `light-dark()` function, so components automatically adapt to user preference. No more `.bg-light__*`/`.bg-dark__*` or `.color-light__*` classes—use `.bg__*` and `.clr__*` with the new variables.

**3. File Breakdown & Use Cases**

* **`main.scss`**
  * **Purpose:** Imports all partials and outputs the compiled CSS.

* **`base/_globals.scss`**
  * **Purpose:** Defines the golden ratio scale, size variables, and all core CSS custom properties for color and spacing.

* **`base/_resets.scss`**
  * **Purpose:** Applies baseline resets and sets default background/text color using CSS variables.

* **`layout/_containers.scss`**
  * **Purpose:** Provides `.container__*` classes for centered, max-width containers.

* **`layout/_grids.scss`**
  * **Purpose:** Provides `.grid` and modifiers for responsive grid layouts.

* **`layout/_sections.scss`**
  * **Purpose:** Adds responsive section padding classes (`.section__xs` to `.section__xl`).

* **`typography/_typography.scss`**
  * **Purpose:** Defines the typographic scale and related classes (e.g., `.display-1`, `.body`). All text color uses `--clr__on-surface` and related variables for theme consistency.

* **`appearance/_background-colors.scss`**
  * **Purpose:** Provides `.bg__*` classes using the new BEM-style CSS variables and `light-dark()` for theme adaptation.

* **`appearance/_shadows.scss`**
  * **Purpose:** Defines shadow mixins using `var(--clr__shadow)`.

* **`sizing/_scale.scss`**
  * **Purpose:** Mixins for fixed width/height using global size variables.

* **`interactivity/_state-layers.scss`**
  * **Purpose:** `.state` class for interactive overlays.

* **`components/_boxes.scss`**
  * **Purpose:** Flexbox layout mixins for horizontal/vertical stacks.

* **`components/_buttons.scss`**
  * **Purpose:** Styles for `.button` and its modifiers, using new color variables for backgrounds and states.

* **`components/_cards.scss`**
  * **Purpose:** Card component styles with dynamic padding and background using the new variable system.

This documentation now reflects the latest BEM-style variable system and modern theming approach. For usage details, see the glossary or refer to the relevant SCSS partials.
