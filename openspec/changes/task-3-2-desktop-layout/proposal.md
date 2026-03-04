## Why

The current mobile-first layout doesn't effectively utilize available screen space on desktop displays, resulting in suboptimal viewing experience and wasted horizontal space.

## What Changes

- Implement responsive grid layouts for Projects section with 2-3 columns on desktop
- Convert Competencies section to grid-based badge layout for desktop
- Add adaptive spacing and padding that scales with screen size
- Establish 600px breakpoint for mobile vs desktop detection
- Ensure single unified layout adapts across all screen sizes without duplication

## Capabilities

### New Capabilities
- `desktop-grid-layout`: Responsive grid system for desktop layouts that adapts to screen width

### Modified Capabilities
- Leave empty - no existing spec requirements changing

## Impact

- Modified screen layout files for Projects and Competencies sections
- Adds MediaQuery dependency for responsive design
- No breaking changes to existing mobile behavior
- Uses existing Flutter layout widgets (LayoutBuilder, Row, Column, Expanded, Flexible)
