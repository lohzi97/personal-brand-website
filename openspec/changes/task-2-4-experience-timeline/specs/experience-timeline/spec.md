## ADDED Requirements

### Requirement: Display Experience Timeline
The system SHALL display a chronological timeline of professional work experience on the Experience section of the website.

#### Scenario: User views Experience section
- **WHEN** user navigates to the Experience section
- **THEN** system displays a chronological list of all professional roles (DotDash Technologies, Crea8 Capital / Celeropes, Freelance)

### Requirement: Display Role Information
The system SHALL display for each role: company name, date range, brief role description, and 2-3 bullet points of measurable impact.

#### Scenario: Role displays complete information
- **WHEN** user views any role in the Experience timeline
- **THEN** system displays company name, date range, role description, and bullet points of achievements

### Requirement: Chronological Order
The system SHALL display professional roles in reverse chronological order (most recent first).

#### Scenario: Roles display in correct order
- **WHEN** user views the Experience timeline
- **THEN** system displays DotDash Technologies (Jan 2025 - Present) first, followed by Crea8 Capital / Celeropes (Jan 2020 - Dec 2024), then Freelance (Ongoing)

### Requirement: Company Website Links
The system SHALL provide clickable links for company names that open the company website in a new browser tab.

#### Scenario: User clicks company name
- **WHEN** user clicks on a company name
- **THEN** system opens the company website URL in a new browser tab

### Requirement: Bullet Points Format
The system SHALL display achievement bullet points in a bulleted list format that is visually distinct from role descriptions.

#### Scenario: Bullet points render correctly
- **WHEN** user views any role in the Experience timeline
- **THEN** system displays achievements as bulleted items (using standard bullet points or circles)

### Requirement: Color Palette Compliance
The system SHALL apply the minimalist color palette (Blue, White, Grey, Black) to the Experience section.

#### Scenario: Experience section uses correct colors
- **WHEN** user views the Experience section
- **THEN** system uses Blue for company names/links, Black/Grey for text, and White for background

### Requirement: Full-Width Layout
The system SHALL display the Experience section at full width on all screen sizes.

#### Scenario: Experience section occupies full width
- **WHEN** user views the Experience section on any device
- **THEN** section spans the full width of the viewport

### Requirement: Responsive Design
The system SHALL adapt the Experience section layout for mobile devices (≤600px breakpoint) while maintaining readability.

#### Scenario: Experience section displays on mobile
- **WHEN** user views the Experience section on a mobile device (≤600px)
- **THEN** system maintains readable text layout and proper spacing without horizontal scrolling

### Requirement: Content from CV.md
The system SHALL display role descriptions and achievements derived from docs/CV.md Sections 2-4.

#### Scenario: Content matches CV.md
- **WHEN** user views the Experience timeline
- **THEN** system displays role information and achievements that accurately reflect the content in docs/CV.md Sections 2-4

### Requirement: No Console Errors
The system SHALL display the Experience section without generating any console errors or warnings.

#### Scenario: Experience section loads successfully
- **WHEN** user navigates to the Experience section
- **THEN** system renders the section without console errors or warnings
