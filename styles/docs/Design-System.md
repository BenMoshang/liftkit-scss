# Design System Documentation

This document provides a comprehensive overview of the SCSS design system, its structure, core concepts, and how to use its various modules.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
- [File Structure](#file-structure)
- [Core Concepts](#core-concepts)
  - [Golden Ratio Scaling (`base/_globals.scss`)](#golden-ratio-scaling-base_globalsscss)
  - [Oklch Adaptive Color System (`appearance/_colors.scss`)](#oklch-adaptive-color-system-appearance_colorsscss)
  - [CSS Custom Properties (Variables)](#css-custom-properties-variables)
- [Module Breakdown](#module-breakdown)
  - [Base (`base/`)](#base-base)
  - [Layout (`layout/`)](#layout-layout)
  - [Spacing (`spacing/`)](#spacing-spacing)
  - [Typography (`typography/`)](#typography-typography)
  - [Appearance (`appearance/`)](#appearance-appearance)
  - [Sizing (`sizing/`)](#sizing-sizing)
  - [State/Interactivity (`state/`)](#stateinteractivity-state)
  - [Components (`components/`)](#components-components)
- [Usage Examples](#usage-examples)

## Introduction

This design system provides a foundational set of styles, components, and utilities built with SCSS. It emphasizes consistency, adaptability (light/dark modes), and a harmonious visual rhythm based on the Golden Ratio.

## File Structure

The system is organized into modules based on CSS properties or component types:

styles/├── main.scss # Main entry point, imports all modules├── base/│ ├── \_globals.scss # Core variables (Golden Ratio, sizes), functions (round-to)│ └──_resets.scss # CSS resets and base element styling├── layout/│ ├── \_containers.scss # Max-width container classes│ ├──_flex.scss # Flexbox utility mixins (flex-row, flex-col, gap)│ ├── \_grids.scss # Grid layout classes│ ├──_sections.scss # Section padding classes│ └── \_stacks.scss # Layering utility classes├── spacing/│ └──_margins.scss # Margin and padding utility mixins (adjust-to, m-, p-)├── typography/│ └── \_typography.scss # Typographic scale classes (display-1, title-a, body, etc.)├── appearance/│ ├──_colors.scss # Oklch adaptive color system (semantic colors, utilities)│ └── \_shadows.scss # Box shadow utility mixins/placeholders├── sizing/│ └──_scale.scss # Generic sizing mixin based on global scale├── state/ # (Note: Imported as 'interactivity' in main.scss)│ └── \_state-layers.scss # Hover/focus/active state overlay styles└── components/├──_buttons.scss # Button component styles├── \_cards.scss # Card component styles└──_boxes.scss # (Note: Referenced but not provided - likely contains h-box/v-box mixins)
_(Note: `main.scss` references `interactivity/state-layers` and `components/boxes`, but the provided files are `state/_state-layers.scss` and `components/_buttons.scss`/`_cards.scss`. Ensure file paths and names are consistent in your project.)_

## Core Concepts

### Golden Ratio Scaling (`base/_globals.scss`)

- **Foundation:** The system uses the Golden Ratio (Phi, ≈ 1.618) to establish harmonious relationships between sizes.
- **Variables:** Key variables like `$MAJOR`, `$MAJOR-HALF`, `$MINOR`, etc., represent proportions derived from Phi.
- **Size Scale:** A base size (`--size-md`, typically `1em`) is defined, and other sizes (`--size-xs`, `--size-lg`, etc.) are calculated as powers of Phi relative to this base. These are available as CSS Custom Properties.
- **Rounding:** The `round-to()` function ensures consistent decimal precision.

### Oklch Adaptive Color System (`appearance/_colors.scss`)

- **Modern Color Space:** Uses Oklch for more perceptually uniform and vibrant colors compared to HSL or RGB.
- **Seed Colors:** A few base `$semantic-seeds` (primary, secondary, error, etc.) and `$surface-seeds` (light/dark backgrounds) are defined.
- **Tonal Palettes:** For each seed, a tonal scale (e.g., 11 steps) is generated using `color-mix(in oklch, ...)`.
- **Adaptive Tokens:** Final CSS variables (e.g., `--primary`, `--on-primary`, `--surface`) use `light-dark()` to automatically switch between appropriate tones based on the user's preferred color scheme (light or dark mode).
- **Contrast:** `--on-<color>` variables (e.g., `--on-primary`) provide accessible text/icon colors for use _on_ their corresponding background color. `--on-surface` uses `color-contrast()` for optimal text contrast against the general background.

### CSS Custom Properties (Variables)

- Extensive use of CSS Custom Properties (e.g., `--size-md`, `--primary`, `--shadow-sm`) allows for:
  - Easy theme customization.
  - Dynamic adjustments (e.g., in JavaScript).
  - Integration with the `light-dark()` mechanism.

## Module Breakdown

### Base (`base/`)

- **`_globals.scss`:** Defines core scaling variables, size tokens (`--size-*`), and the `round-to()` function.
- **`_resets.scss`:** Applies modern CSS resets (`box-sizing: border-box`, margin/padding removal), basic element styling (links, media), and sets up the adaptive background color (`--background`) and scrollbar styles.

### Layout (`layout/`)

- **`_containers.scss`:** Provides `.container__*` classes (`xs` to `xl`) to constrain content width.
- **`_flex.scss`:** Offers SCSS mixins for creating flexbox layouts:
  - `@include flex-row($gap-size)` / `@include flex-col($gap-size)`: Block-level flex containers.
  - `@include inline-flex-row($gap-size)` / `@include inline-flex-col($gap-size)`: Inline-level flex containers.
  - `$gap-size`: Optional (e.g., `xs`, `sm`, `md`). Accepts quoted or unquoted keys.
- **`_grids.scss`:** Basic grid classes (`.grid`, `.grid--xs` to `.grid--2xl` for gap) and column/row count helpers (`.col__1` to `.col__9`, `.row__1` to `.row__9`).
- **`_sections.scss`:** `.section__*` classes (`xs` to `xl`) for applying vertical and horizontal padding to page sections, with responsive adjustments.
- **`_stacks.scss`:** Utility classes for creating layered layouts using CSS Grid (`.stack`, `.stack__layer`, `.stack__layer--float`, `.stack__layer--above`, `.stack__layer--below`).

### Spacing (`spacing/`)

- **`_margins.scss`:** Defines CSS variables (`--xs` to `--2xl`) based on the current line height and provides mixins for applying margin and padding:
  - `@include adjust-to($line-height)`: Sets the spacing variables relative to a line height. Applied in `:root` via `_typography.scss`.
  - `@include m-[direction]__[size]` (e.g., `@include m-top__md`, `@include m-horizontal__sm`)
  - `@include p-[direction]__[size]` (e.g., `@include p-bottom__lg`, `@include p-vertical__xs`)

### Typography (`typography/`)

- **`_typography.scss`:**
  - Defines typographic scale classes (`.display-1`, `.title-a`, `.heading`, `.body`, `.label`, etc.).
  - Each class sets `font-size`, `line-height`, `letter-spacing`, and sometimes `font-weight`.
  - Includes `--bold` modifiers (e.g., `.heading--bold`).
  - Applies base font styles and responsive adjustments to the type scale.
  - Uses the `margins.adjust-to()` mixin to link spacing variables to line heights.

### Appearance (`appearance/`)

- **`_colors.scss`:** The core of the adaptive color system. Defines `--seed-*`, generates tonal scales, and outputs final semantic tokens (`--primary`, `--on-primary`, `--surface`, etc.) using `light-dark()`. Also provides utility classes like `.text--primary`, `.bg--primary`, `.bg--primary-container`.
- **`_shadows.scss`:** Defines shadow tokens (`--shadow-xs` to `--shadow-2xl`) and placeholder selectors (`%shadow__xs`, etc.) or a mixin (`@include apply-shadow($size)`) for applying them.

### Sizing (`sizing/`)

- **`_scale.scss`:** Provides a generic `@include inline-size($prop, $key)` mixin to apply sizes from the global scale map (defined via `--size-*` variables) to any CSS property (e.g., `width`, `height`). Keys range from `2xs` to `3xl`.

### State/Interactivity (`state/`)

- **`_state-layers.scss`:** Creates a `.state` class intended to be nested inside interactive elements (like buttons). It provides a subtle background overlay on `:hover`, `:active`, and `:focus-visible` states.

### Components (`components/`)

- **`_buttons.scss`:** Styles for `.button` elements. Includes modifiers for fill (`.button--fill`), outline (`.button--outline`), icons (`.button--start-icon`, `.button--end-icon`), and size (`.button--large`). Uses the `h-box` mixin (presumably from `_boxes.scss`) for icon/text layout. Requires the `.state` element nested inside for interaction feedback.
- **`_cards.scss`:** Styles for `.card` elements. Features automatic padding calculation based on the largest typography class inside using `:has()` (with fallbacks and explicit modifiers like `.card--title-a`). Uses `--card-scale-factor` internally. Requires the `.state` element nested inside for interaction feedback if desired.
- **`_boxes.scss` (Assumed):** Likely contains mixins like `@include h-box($gap-size)` and `@include v-box($gap-size)` which are wrappers around the flexbox mixins from `_flex.scss` for common horizontal/vertical layout patterns.

## Usage Examples

```html
<button class="button button--fill">
  <span class="button__content">
    <span class="button__icon"> </span>
    <span>Primary Button</span>
  </span>
  <span class="state"></span>
</button>

<button class="button button--outline">
  <span class="button__content">Outline Button</span>
  <span class="state"></span>
</button>

<div class="card card--heading">
  <h3 class="heading">Card Title</h3>
  <p class="body">
    This card's padding is scaled based on the 'heading' text size.
  </p>
  <button class="button">Action</button>
  <span class="state"></span>
</div>

<section class="section__md">
  <div class="container__md">
    <div class="grid grid--lg col__3">
      <div class="card">
        <p class="body">Item 1</p>
        <span class="state"></span>
      </div>
      <div class="card">
        <p class="body">Item 2</p>
        <span class="state"></span>
      </div>
      <div class="card">
        <p class="body">Item 3</p>
        <span class="state"></span>
      </div>
    </div>
  </div>
</section>

<h1 class="display-1">Main Page Title</h1>
<p class="body">This is standard body text.</p>
<p class="caption">A small caption below.</p>

<p class="text--primary">This text uses the primary color.</p>
<div class="bg--secondary-container">
  <p>This content is inside a secondary container background.</p>
</div>
```
