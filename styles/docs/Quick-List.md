# Design System - Usage Quick List

Core classes and mixins for applying the design system:

**Layout:**

* Containers: `.container__[xs-xl]`
* Sections: `.section__[xs-xl]`
* Grid: `.grid`, `.grid--[xs-2xl]`, `.col__[1-9]`
* Flex (Mixin): `@include flex-row/col($gap?)`, `@include inline-flex-row/col($gap?)`
* Stack: `.stack`, `.stack__layer`, `.stack__layer--[float|above|below]`

**Typography:**

* Text Styles: `.display-[1-2]`, `.title-[a-c]`, `.heading`, `.subheading`, `.body`, `.callout`, `.label`, `.caption`, `.overline`
* Bold Modifier: `.--bold`

**Color:**

* Text: `.text--[primary|secondary|...]`, `.text--surface`
* Background (w/ text): `.bg--[primary|secondary|...]`, `.bg--surface`
* Container BG: `.bg--[primary|secondary|...]-container`
* CSS Variables: `var(--primary)`, `var(--on-surface)`, etc.

**Spacing (Mixins):**

* Margin: `@include m-[direction]__[size]`
* Padding: `@include p-[direction]__[size]`

**Components:**

* Button: `.button`, `.button--[fill|outline|start-icon|end-icon|large]` (Requires inner `.button__content`, `.button__icon`, `.state`)
* Card: `.card`, `.card--[display-1|title-a|...]` (Auto-padding or explicit. Requires inner `.state` for interaction)

**Appearance:**

* Shadows (Mixin/Extend): `@include apply-shadow([xs-2xl])` / `%shadow__[xs-2xl]`
* Shadows (CSS): `var(--shadow-[xs-2xl])`

**State Layer (for interactions):**

* Add `<span class="state"></span>` inside interactive elements.

**Generic Sizing (Mixin):**

* `@include size($property, [2xs-3xl])`
