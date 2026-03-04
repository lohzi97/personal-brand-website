## ADDED Requirements

### Requirement: Display competencies section with 4 skill categories
The system SHALL display a competencies section with 4 skill categories, each containing relevant technical skills as badge-style tags.

#### Scenario: View competencies section on desktop
- **WHEN** user views the competencies section on a desktop screen (>600px width)
- **THEN** the system displays all 4 categories in a 2x2 grid layout with appropriate spacing

#### Scenario: View competencies section on mobile
- **WHEN** user views the competencies section on a mobile screen (≤600px width)
- **THEN** the system displays all 4 categories vertically stacked with appropriate spacing

### Requirement: Display Languages category with 8 programming languages
The system SHALL display a Languages category containing the following skills: Python, Java, JavaScript, VBA, MATLAB, C, C++, C# as individual badge-style tags.

#### Scenario: View Languages category
- **WHEN** user views the Languages category
- **THEN** the system displays 8 badge tags: Python, Java, JavaScript, VBA, MATLAB, C, C++, C#

### Requirement: Display Frameworks category with 4 frameworks
The system SHALL display a Frameworks category containing the following skills: Django, Spring Boot, NodeJS, Flutter as individual badge-style tags.

#### Scenario: View Frameworks category
- **WHEN** user views the Frameworks category
- **THEN** the system displays 4 badge tags: Django, Spring Boot, NodeJS, Flutter

### Requirement: Display Databases & Cloud category with 5 technologies
The system SHALL display a Databases & Cloud category containing the following skills: MySQL, Redis, SQLite, GCP, Firebase as individual badge-style tags.

#### Scenario: View Databases & Cloud category
- **WHEN** user views the Databases & Cloud category
- **THEN** the system displays 5 badge tags: MySQL, Redis, SQLite, GCP, Firebase

### Requirement: Display DevOps & Tools category with 6 tools
The system SHALL display a DevOps & Tools category containing the following skills: Docker, k8s, Jenkins, GlitchTip, n8n, Linux as individual badge-style tags.

#### Scenario: View DevOps & Tools category
- **WHEN** user views the DevOps & Tools category
- **THEN** the system displays 6 badge tags: Docker, k8s, Jenkins, GlitchTip, n8n, Linux

### Requirement: Badge tags styled consistently
The system SHALL style all badge tags consistently with the minimalist color palette (Blue, White, Grey, Black) and proper spacing.

#### Scenario: View badge tag styling
- **WHEN** user views any badge tag
- **THEN** the system displays the tag with rounded corners, consistent padding, and colors from the minimalist palette

### Requirement: Category headers styled with Blue
The system SHALL style category headers using Blue from the color palette for visual hierarchy.

#### Scenario: View category header
- **WHEN** user views any category header
- **THEN** the system displays the header in Blue color text

### Requirement: Competencies section positioned below Hero section
The system SHALL position the competencies section immediately below the Hero section in the single-page layout.

#### Scenario: Scroll from Hero to Competencies
- **WHEN** user scrolls down from the Hero section
- **THEN** the system displays the competencies section immediately below the Hero section

### Requirement: Responsive breakpoint at 600px
The system SHALL use a 600px breakpoint to switch between desktop and mobile layouts.

#### Scenario: Layout switches at breakpoint
- **WHEN** screen width changes from 601px to 600px
- **THEN** the system switches from desktop grid layout to mobile stacked layout

### Requirement: Hot reload support
The system SHALL support hot reload without errors when changes are made to the competencies section.

#### Scenario: Hot reload after modifying competencies
- **WHEN** developer modifies the competencies section code and triggers hot reload
- **THEN** the system applies changes without errors or crashes

### Requirement: No console errors
The system SHALL render the competencies section without any console errors.

#### Scenario: View competencies in browser console
- **WHEN** user views the competencies section with browser developer console open
- **THEN** no errors are logged to the console
