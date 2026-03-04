## ADDED Requirements

### Requirement: Desktop screen detection
The system SHALL detect desktop screens when screen width is greater than 600px.

#### Scenario: Mobile screen detection
- **WHEN** screen width is 600px or less
- **THEN** system displays mobile layout with single-column layout

#### Scenario: Desktop screen detection
- **WHEN** screen width is greater than 600px
- **THEN** system displays desktop layout with multi-column grid layout

### Requirement: Projects grid layout on desktop
The system SHALL display Projects in a 2-3 column grid when on desktop screens.

#### Scenario: Projects display in grid at 1920px width
- **WHEN** screen width is 1920px
- **THEN** Projects section displays projects in a 2-3 column grid layout

#### Scenario: Projects grid uses available width
- **WHEN** Projects section renders on desktop
- **THEN** grid columns expand to use available horizontal space evenly

#### Scenario: Projects remain single column on mobile
- **WHEN** screen width is 600px or less
- **THEN** Projects section displays in single column layout

### Requirement: Competencies grid layout on desktop
The system SHALL display Competencies in a grid of badges when on desktop screens.

#### Scenario: Competencies display in grid at 1920px width
- **WHEN** screen width is 1920px
- **THEN** Competencies section displays badges in a multi-row grid layout

#### Scenario: Competencies badges wrap appropriately
- **WHEN** Competencies section renders on desktop
- **THEN** badges wrap to new rows based on available space

#### Scenario: Competencies remain stacked on mobile
- **WHEN** screen width is 600px or less
- **THEN** Competencies section displays badges in single-column stack

### Requirement: Adaptive spacing and padding
The system SHALL adjust spacing and padding proportionally based on screen size.

#### Scenario: Spacing scales with screen width
- **WHEN** screen width increases from mobile to desktop
- **THEN** horizontal and vertical spacing values increase proportionally to screen size

#### Scenario: No excessive whitespace on desktop
- **WHEN** screen width is 1920px
- **THEN** spacing and padding prevent excessive whitespace gaps in layout

#### Scenario: No cramped content on mobile
- **WHEN** screen width is 600px or less
- **THEN** spacing and padding prevent content from appearing cramped or overlapping

### Requirement: Single unified layout
The system SHALL use a single layout implementation that adapts across all screen sizes without code duplication.

#### Scenario: Layout adapts without separate implementations
- **WHEN** layout renders at any screen size
- **THEN** same layout codebase responds to screen width changes

#### Scenario: No separate mobile/desktop screen files
- **WHEN** implementing responsive layout
- **THEN** system uses conditional rendering within same widget rather than separate screen files
