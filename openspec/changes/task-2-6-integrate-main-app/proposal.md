## Why

The section widgets created in previous tasks need to be integrated into a cohesive single-page application. Currently, sections are implemented in isolation and need to be assembled into the main entry point with proper scrolling behavior and consistent theming.

## What Changes

- Update `lib/main.dart` to import and integrate all section widgets (Hero, Competencies, Projects, Experience, Contact)
- Implement single-page scrolling layout using `SingleChildScrollView`
- Apply consistent color theme (Blue, White, Grey, Black) across all sections
- Configure smooth scrolling behavior for wheel and touch interactions
- Ensure responsive design with no horizontal scrolling (600px breakpoint)

## Capabilities

### New Capabilities

- `main-app-structure`: Single-page application layout that integrates all section widgets in a vertical scrolling container
- `smooth-scrolling`: Scroll behavior configuration for smooth transitions between sections using wheel and touch gestures
- `app-theming`: Consistent application-wide color theme using Blue, White, Grey, and Black palette
- `responsive-layout`: Adaptive layout that prevents horizontal scrolling across mobile and desktop (600px breakpoint)

### Modified Capabilities

None - this is initial application structure.

## Impact

- Primary code change: `lib/main.dart` (main application entry point)
- Dependencies: All existing section widgets (Hero, Competencies, Projects, Experience, Contact)
- No external dependencies or API changes
- No breaking changes to existing functionality
