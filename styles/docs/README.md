# LiftKit SCSS

A fork of LiftKit CSS utilizing the power of the CSS preprocessor Sass to
enhance the original where possible, focusing on consistency and ease of use. I
am pleased to announce that LiftKit SCSS is stable and already out in the wild.

Huge thanks to [@chainlift](https://www.github.com/chainlift) for designing
LiftKit, a design system utilizing the golden ratio to provide an
oddly-satisfying look and feel.

## Overview

The aim of the fork is not to provide a drag-and-drop replacement for LiftKit
CSS. This means that LiftKit SCSS is *not* compatible with LiftKit CSS out of
the box.

LiftKit SCSS uses mixins in favor of non-semantic class names in order to
achieve a significantly smaller footprint and encourage semantic naming of
classes in the DOM. Due to this, the following utility classes of LiftKit CSS
are only available in LiftKit SCSS using the `@include`-at rule:

- Margins (such as `m-top__sm`) and padding (such as `p-bottom__md`). Note the
  shortening of `pad` to just `p`.
- Shadows (such as `shadow__md`). Note the name change for consistency.
- Boxes (such as `h-box` or `v-inline__sm`). Note the name change for
  consistency.
- Font and background colors (such as `bg__error` or `fg__primary`).
- Sizes for both width and height via the generic `size` mixin: `@include sizes.size(width, <size>)` and `@include sizes.size(height, <size>)` (sizes range from `2xs` to `3xl`). Replace legacy `w__*`/`h__*` mixins with this new pattern.

Note that the step size variables such as `--wholestep` (equal to `$MAJOR`) or
`--wholestep-dec` (equal to `$MINOR`) are now only available at compile-time.

Containers and sections also adhere to the naming convention involving the size
suffix (`__xs`, `__sm`, `__md`, `__lg`, `__xl`) for consistency.

## Quickstart

Already familiar with LiftKit and Sass? Then download the latest release of
LitKit SCSS from
[GitHub](https://github.com/Theikon/liftkit-scss/releases/download/v1.1.X/liftkit-v1.1.0.zip),
and import the `liftkit.scss` file for example as follows:

```SCSS
@use "liftkit";

nav {
  @include liftkit.h-box__md;
  @include liftkit.bg__surface-container;

  align-items: center;
}

p {
  @include liftkit.m-bottom__sm;
}
```
Note that LiftKit SCSS uses [Inter](https://rsms.me/inter/) throughout its font
styles, which is freely available on Google Fonts. LiftKit SCSS ships with the
Material 3 [baseline](https://m3.material.io/styles/color/static/baseline)
color scheme by default. Feel free to design a unique color scheme using the
[Material Theme Builder](https://material-foundation.github.io/material-theme-builder/).

In case you are new to LiftKit in general, have a look at the official
documentation behind the design philosophy over at
[Chainlift](https://www.chainlift.io/liftkitdocs/overview).
