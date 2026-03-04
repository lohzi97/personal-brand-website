## Context

The application currently uses a mobile-first single-column layout that doesn't adapt to larger desktop screens. The Projects and Competencies sections waste horizontal space on desktop displays by stacking content vertically. The application is built with Flutter and uses standard layout widgets.

## Goals / Non-Goals

**Goals:**
- Implement responsive grid layouts that adapt to screen width
- Use 600px breakpoint to distinguish mobile from desktop
- Ensure Projects display in 2-3 columns on desktop
- Ensure Competencies display in a grid of badges on desktop
- Maintain spacing and padding proportions across screen sizes
- Keep a single unified layout without duplicating code for mobile/desktop

**Non-Goals:**
- Creating separate screen files for mobile and desktop
- Implementing complex media query libraries
- Adding new dependencies beyond standard Flutter widgets
- Creating a reusable grid widget library (future consideration)

## Decisions

**Use MediaQuery for responsive detection**
- Chose MediaQuery.of(context).size.width over LayoutBuilder because we need global screen width information
- Alternative: LayoutBuilder could work but requires wrapping more widgets; MediaQuery provides simpler access to screen dimensions

**600px breakpoint for mobile vs desktop**
- Chose 600px as it's a common breakpoint used in web design and aligns with tablet portrait dimensions
- Alternatives considered: 768px (tablet landscape), 1024px (desktop) - both too high for this use case

**Grid layouts using Row/Column with Expanded**
- Chose standard Flutter widgets (Row, Column, Expanded, Flexible) over third-party packages
- Alternative: flutter_staggered_grid_view could provide more complex layouts but adds dependency overhead for this use case

**Adaptive spacing using screen width percentage**
- Chose calculating spacing based on MediaQuery.of(context).size.width * 0.02-0.04 for proportional scaling
- Alternative: Fixed spacing values don't scale well across different screen sizes

## Risks / Trade-offs

[Risk] Inconsistent spacing across different sections
→ Mitigation: Define spacing constants that scale proportionally (e.g., `kSpacing = MediaQuery.of(context).size.width * 0.03`)

[Risk] Layout may break on ultra-wide monitors (>1920px)
→ Mitigation: Use `ConstrainedBox` to constrain maximum width and prevent content from stretching too far

[Trade-off] Single layout codebase may become complex with multiple conditionals
→ Mitigation: Keep responsive logic focused in layout widgets; avoid deeply nested conditionals by extracting layout components
