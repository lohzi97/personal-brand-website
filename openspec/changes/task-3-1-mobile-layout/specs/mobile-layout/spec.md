## ADDED Requirements

### Requirement: Mobile breakpoint detection
The system SHALL detect mobile screens using MediaQuery to check if the screen width is less than or equal to 600px.

#### Scenario: Desktop screen detected
- **WHEN** the screen width is greater than 600px
- **THEN** the system SHALL render the desktop layout

#### Scenario: Mobile screen detected
- **WHEN** the screen width is less than or equal to 600px
- **THEN** the system SHALL render the mobile layout

#### Scenario: Breakpoint boundary at 600px
- **WHEN** the screen width is exactly 600px
- **THEN** the system SHALL treat the screen as mobile

### Requirement: Hero section mobile layout
The system SHALL center the Hero section content on mobile screens with vertical stacking.

#### Scenario: Hero content centers on mobile
- **WHEN** the screen width is 375px
- **THEN** the Hero section SHALL center all content horizontally
- **AND** the Hero section SHALL stack text and elements vertically

#### Scenario: Hero uses desktop layout on large screen
- **WHEN** the screen width is 1024px
- **THEN** the Hero section SHALL use the desktop layout without centering

### Requirement: Competencies section mobile layout
The system SHALL stack Competencies categories vertically on mobile screens instead of using horizontal layouts.

#### Scenario: Competencies stack vertically on mobile
- **WHEN** the screen width is 375px
- **THEN** the Competencies categories SHALL be arranged in a single vertical column
- **AND** each category SHALL expand to fill available width

#### Scenario: Competencies use desktop layout on large screen
- **WHEN** the screen width is 1024px
- **THEN** the Competencies categories SHALL use horizontal arrangement

### Requirement: Projects section mobile layout
The system SHALL display Projects as single column cards on mobile screens instead of multi-column grid.

#### Scenario: Projects show single column on mobile
- **WHEN** the screen width is 375px
- **THEN** the Projects section SHALL display cards in a single vertical column
- **AND** each project card SHALL expand to full width

#### Scenario: Projects use grid layout on large screen
- **WHEN** the screen width is 1024px
- **THEN** the Projects section SHALL use multi-column grid layout

### Requirement: Experience section mobile layout
The system SHALL display Experience timeline at full width on mobile screens.

#### Scenario: Experience uses full width on mobile
- **WHEN** the screen width is 375px
- **THEN** the Experience section SHALL use full width for all content
- **AND** no horizontal scrolling SHALL be required

#### Scenario: Experience uses desktop layout on large screen
- **WHEN** the screen width is 1024px
- **THEN** the Experience section SHALL use the desktop layout with proper spacing

### Requirement: Contact section mobile layout
The system SHALL stack Contact links vertically on mobile screens instead of horizontal arrangement.

#### Scenario: Contact links stack vertically on mobile
- **WHEN** the screen width is 375px
- **THEN** the Contact links SHALL be stacked vertically
- **AND** each link SHALL be easily tappable with adequate spacing

#### Scenario: Contact links use horizontal layout on large screen
- **WHEN** the screen width is 1024px
- **THEN** the Contact links SHALL be arranged horizontally

### Requirement: No horizontal scrolling on mobile
The system SHALL prevent horizontal scrolling on mobile screens at any width.

#### Scenario: No horizontal scroll at 375px
- **WHEN** the screen width is 375px and the user scrolls horizontally
- **THEN** the system SHALL not allow horizontal scrolling
- **AND** all content SHALL fit within the viewport width

#### Scenario: No horizontal scroll at 600px
- **WHEN** the screen width is 600px and the user scrolls horizontally
- **THEN** the system SHALL not allow horizontal scrolling

### Requirement: Text readability on mobile
The system SHALL ensure all text remains readable on mobile screens without overflow or truncation.

#### Scenario: Text is readable on mobile
- **WHEN** the screen width is 375px
- **THEN** all text SHALL be fully visible without horizontal scrolling
- **AND** text SHALL not overflow containers or get truncated

#### Scenario: Long text wraps properly on mobile
- **WHEN** a section contains long text at 375px width
- **THEN** the text SHALL wrap to multiple lines
- **AND** no text SHALL extend beyond the screen width
