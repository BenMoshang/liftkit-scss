# Changelog

All notable changes to this project are documented in this file.

## [Unreleased] - 2025-04-20

### Changed
- **Containers**: Refactored `styles/layout/_containers.scss` to use a `$container-scales` map with an `@each` loop and a `@mixin container-base`, replacing manual `&__*` blocks and `@extend`.
- **Sizing**: Updated `styles/sizing/_width.scss` to unify width and height utilities under a generic `@mixin size` and `$size-map`, auto-generating `.w-*` and `.h-*` classes.
- **Gaps**: Simplified `styles/spacing/_gaps.scss` by removing `@use 'sass:string'` and `sass:meta`, dropping the internal helper, and using `@mixin gap()` with `map.has-key()`.
- **Spacing**: Drafted a loop-based generator in `styles/spacing/_margins.scss` to replace manual margin/padding classes, iterating over shorthands, sides, and spacing keys.

### Removed
- `@extend .container` usages in `_containers.scss`.
- Deprecated `@mixin inline-size()` and old `$scale-map` in `_width.scss`.
- Internal `_apply-flex-gap()` mixin and unused imports in `_gaps.scss`.

### Next Steps
- Refactor grid utilities (migrate to new grid-cols/grid-rows system with responsive variants)
- Add central `@forward` index files for each directory
- Generate responsive variants for all utilities using breakpoints mixin
- Clean up unused imports across all SCSS modules
- Add standardized file headers to all SCSS files
