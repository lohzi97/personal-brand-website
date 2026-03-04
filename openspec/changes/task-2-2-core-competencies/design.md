## Context

The personal brand website is a single-page Flutter application that currently displays a Hero section. The project follows a minimalist design with a color palette of Blue, White, Grey, and Black. The website is built using Flutter widgets and implements responsive design with a breakpoint at 600px to distinguish between mobile and desktop layouts. The existing codebase uses standard Flutter widgets like `Row`, `Column`, `Expanded`, and `Flexible` for responsive layouts.

## Goals / Non-Goals

**Goals:**
- Create a competencies section that displays technical skills in 4 categorized groups
- Implement badge-style tags with consistent styling
- Ensure the section displays below the Hero section with smooth scrolling
- Apply the existing minimalist color palette
- Implement responsive design that adapts to mobile (≤600px) and desktop (>600px) breakpoints
- Ensure hot reload works and no console errors occur

**Non-Goals:**
- No external dependencies or new packages
- No animation or interaction beyond basic hover states
- No sorting or filtering of skills
- No integration with external APIs or data sources

## Decisions

**Flutter Widget Choice:**
- Use `Wrap` widget for badge tags to handle wrapping naturally across different screen widths
- Use `Chip` or custom `Container` widgets for badge styling to maintain control over appearance
- Use `Row` with `Expanded`/`Flexible` for category layout on desktop, switch to `Column` on mobile

**Layout Structure:**
- On desktop (>600px): Use `Row` to display categories side-by-side with 2 columns (2x2 grid)
- On mobile (≤600px): Use `Column` to display categories vertically stacked
- Use `LayoutBuilder` or `MediaQuery` to detect screen width and switch layouts

**Styling Approach:**
- Apply Blue for category headers to match color palette
- Use Grey or Black for badge backgrounds with White text for contrast
- Implement consistent padding and spacing across all elements
- Use `BoxDecoration` with `borderRadius` for rounded badges

**Data Source:**
- Hardcode skill data directly in the component (no external data fetching)
- Keep data structure as lists of strings for simplicity

## Risks / Trade-offs

**Risk:** Badge overflow on very small screens with long skill names
**Mitigation:** Use `Wrap` widget with appropriate spacing and `runSpacing` to ensure tags wrap gracefully

**Trade-off:** Hardcoding skills vs dynamic data
**Rationale:** Skills are relatively stable; hardcoding reduces complexity and eliminates need for external data management. Future changes can be made directly in code.

**Risk:** Inconsistent spacing across different screen sizes
**Mitigation:** Use responsive padding based on screen width, test on multiple breakpoints

## Migration Plan

No migration required as this is a new component. Implementation steps:
1. Create `lib/pages/competencies_section.dart` with basic structure
2. Implement widget with hardcoded skill data
3. Add responsive layout logic
4. Style badges and categories according to design
5. Integrate into main page layout below Hero section
6. Test with `flutter run -d chrome` and verify hot reload works

## Open Questions

None identified at this time.
