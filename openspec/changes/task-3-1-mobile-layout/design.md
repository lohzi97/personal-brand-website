## Context

The personal brand website is currently designed only for desktop breakpoints with no mobile responsiveness. The app uses Flutter widgets but lacks adaptive layouts for smaller screens. With mobile traffic comprising 50%+ of web traffic, the site is inaccessible to mobile users. The Flutter application structure uses a single main widget tree with separate section widgets (Hero, Competencies, Projects, Experience, Contact) that currently assume desktop layouts.

## Goals / Non-Goals

**Goals:**
- Implement responsive layouts that adapt at 600px breakpoint using MediaQuery
- Ensure all sections (Hero, Competencies, Projects, Experience, Contact) display correctly on mobile
- Prevent horizontal scrolling on mobile devices
- Maintain text readability on mobile screens
- Use existing Flutter widgets (MediaQuery, LayoutBuilder) without new dependencies

**Non-Goals:**
- Creating separate mobile-specific page routes
- Touch gesture optimizations beyond basic layout
- Mobile-specific animations or transitions
- Support for tablets or other intermediate breakpoints (desktop only: >600px, mobile only: ≤600px)
- Dynamic font sizing adjustments (text remains readable at current sizes)

## Decisions

**Breakpoint Selection (600px)**
- 600px chosen as the mobile breakpoint to align with common mobile device widths (375px-428px for modern phones)
- Alternative considered: 768px (tablet breakpoint) - rejected as too wide for distinguishing mobile phones
- Alternative considered: 480px - rejected as too narrow, would miss some larger phones
- 600px provides clear separation between mobile phones and desktop/tablet displays

**Use of MediaQuery**
- Selected MediaQuery.of(context).size.width for screen width detection
- Alternative considered: LayoutBuilder only - rejected as MediaQuery provides direct access to screen dimensions and is Flutter's recommended approach
- Alternative considered: External breakpoint package - rejected as unnecessary dependency for single breakpoint
- MediaQuery is built-in, well-tested, and provides all needed functionality

**Single Column Layout on Mobile**
- All sections convert to single column vertical stacking on mobile
- Alternative considered: Grid layouts for some sections - rejected for complexity and consistency
- Alternative considered: Horizontal scrolling for some sections - rejected as poor UX on mobile
- Single column provides consistent, predictable mobile experience

**Layout Pattern: Row/Column with Expanded/Flexible**
- Use Row/Column widgets with Expanded/Flexible for flexible layouts
- Alternative considered: AspectRatio constraints - rejected as too rigid
- Alternative considered: Fixed pixel values - rejected as doesn't adapt
- Flutter's standard approach allows smooth transitions between breakpoints

**Testing Approach: Browser Dev Tools at 375px**
- Test using Chrome DevTools at 375px width (iPhone SE/mini viewport)
- Alternative considered: Multiple mobile widths - rejected as 375px covers common worst case
- Alternative considered: Physical device testing - rejected as not accessible in CI
- 375px is a reasonable proxy for mobile validation

## Risks / Trade-offs

**Layout Breakage in Complex Widgets** → Mitigation: Test each section individually, validate no horizontal scrolling at 375px, use SizedBox to constrain widths

**Text Readability on Small Screens** → Mitigation: Ensure minimum text sizes, test at 375px, verify text doesn't overflow containers

**MediaQuery Context Issues** → Mitigation: Ensure all responsive widgets have proper BuildContext, use LayoutBuilder where context might be unavailable

**Inconsistent Mobile Experience** → Mitigation: Define consistent mobile layout pattern (vertical stacking, single column), apply pattern uniformly across sections

**Overly Complex Conditional Logic** → Mitigation: Create helper widgets for common mobile patterns (e.g., `isMobile` check), extract mobile layout logic into separate widgets
