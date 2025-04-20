# Typography

## General

> “I think about typography in a weird way. I think about hierarchy in three dimensions instead of two.”

Most systems explain hierarchy as “what the viewer reads first.” LiftKit extends this by imagining depth—almost “looking into” the interface. As VR/AR evolve, you might swim through information instead of scroll. LiftKit lays that 3D foundation today.

### The Type System

LiftKit defines one scale with two weight‑families (regular and bold). Each class specifies default/emphasized weights, size (in vw), line‑height, and letter‑spacing:

| Class       | Wt (400) | Wt (Emph.) | Size   | Line‑Height | Letter Spacing |
|-------------|----------|------------|--------|-------------|----------------|
| display1    | 400      | 700        | 4.235  | 1.129       | -0.022         |
| display2    | 400      | 700        | 2.618  | 1.272       | -0.022         |
| title1      | 400      | 700        | 2.058  | 1.272       | -0.022         |
| title2      | 400      | 600        | 1.618  | 1.272       | -0.020         |
| title3      | 400      | 600        | 1.272  | 1.272       | -0.017         |
| heading     | 600      | 700        | 1.129  | 1.272       | -0.014         |
| subheading  | 400      | 600        | 0.885  | 1.272       | -0.007         |
| body        | 400      | 600        | 1      | 1.618       | -0.011         |
| callout     | 400      | 600        | 0.943  | 1.272       | -0.009         |
| label       | 500      | 700        | 0.835  | 1.272       | -0.004         |
| caption     | 400      | 600        | 0.786  | 1.272       | -0.007         |
| overline    | 400      | 600        | 0.786  | 1.272       |  0.0618        |

### Responsiveness

Root font‑size = 1 vw; guardrails use media queries to keep fonts accessible on small screens. For example:

```scss
@media (max-width: 600px) {
  .display1 { font-size: 10vw; }
  .display2 { font-size: 6.5vw; }
  // …etc.
}
```

On mobile, `.display1`/`.display2` use smaller steps to fit real estate.

### Scaling Logic

- Asymmetrical steps: larger sizes scale by ~1.618×, smaller by ~1.06×.
- Pure golden‑ratio scaling yields too few sizes; smaller ratios yield too many.
- LiftKit blends Apple HIG (prescriptive) and Material 3 (suggestive) to balance clarity and flexibility.

## Code Snippets

### Global Media Queries

```scss
// Example guardrails
@media (max-width: 400px) {
  :root { font-size: 0.9vw; }
}
@media (min-width: 1000px) {
  :root { font-size: 1.1vw; }
}
```

### Utility Mixins

```scss
@mixin text-style($class) {
  @if $class == display1 {
    font-size: 4.235vw; font-weight: 400; line-height: 1.129;
  }
  // …other cases…
}

h1 { @include text-style(display1); }
```

## Recommended Use

- **Antialiasing**: keep global defaults for crisp text.
- **Combining styles**: skip upwards (e.g. `.title3` → `.display1`), but don’t skip downward (e.g. `.heading` → `.body`).
- **Spacing**: use LiftKit text‑utility classes, not spacing variables.
- **Font families**: max 2–3; use one for related roles to preserve a “golden lattice.”
- **Custom styles**: can insert between existing ones but ≥`.caption`; scale by φ-derived factors (1.618, 1.272, 1.128, 1.062).

## Accessibility & Color Grading

- Text color grading helps hierarchy but can break WCAG. Apple’s tertiary/quaternary labels often fail contrast checks.
- LiftKit omits low‑contrast labels; if you must, control via opacity—not static colors—and test in both light/dark modes.

---

### Summary

LiftKit’s typography system merges the best of Apple HIG and Material 3:
1. A single asymmetric scale rooted in the golden ratio.
2. Two weight families for emphasis.
3. Responsive guardrails via media queries.
4. Clear naming and limited flexibility to minimize mistakes.
5. Utility mixins for easy application.

This approach covers diverse use‑cases with minimal classes and a robust 3D‑inspired hierarchy foundation.
