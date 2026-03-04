## ADDED Requirements

### Requirement: Display Email Contact Link
The system SHALL display an email contact link using mailto: protocol that opens the user's default email client when clicked.

#### Scenario: User clicks email link
- **WHEN** user clicks on the email contact link
- **THEN** system launches the default email client with lohzian@live.com as the recipient

### Requirement: Display GitHub Contact Link
The system SHALL display a GitHub profile link that navigates to the correct GitHub profile when clicked.

#### Scenario: User clicks GitHub link
- **WHEN** user clicks on the GitHub contact link
- **THEN** system opens https://github.com/lohzi97 in a new browser tab

### Requirement: Display LinkedIn Contact Link
The system SHALL display a LinkedIn profile link that navigates to the correct LinkedIn profile when clicked.

#### Scenario: User clicks LinkedIn link
- **WHEN** user clicks on the LinkedIn contact link
- **THEN** system opens https://www.linkedin.com/in/loh-zi-jian/ in a new browser tab

### Requirement: Contact Section Layout on Desktop
The system SHALL display contact links in a horizontal row layout on desktop screens (width > 600px).

#### Scenario: View contact section on desktop
- **WHEN** user views the contact section on a desktop screen (width > 600px)
- **THEN** contact links are displayed horizontally in a row
- **AND** all three links are visible without scrolling

### Requirement: Contact Section Layout on Mobile
The system SHALL display contact links in a vertical column layout on mobile screens (width ≤ 600px).

#### Scenario: View contact section on mobile
- **WHEN** user views the contact section on a mobile screen (width ≤ 600px)
- **THEN** contact links are displayed vertically in a column
- **AND** links are stacked from top to bottom

### Requirement: Contact Section Positioning
The system SHALL position the contact section at the bottom of the page as a footer area.

#### Scenario: Scroll to bottom of page
- **WHEN** user scrolls to the bottom of the page
- **THEN** contact section is visible as the footer
- **AND** contact section appears after all other page content

### Requirement: Contact Section Styling
The system SHALL apply the minimalist color palette (Blue, White, Grey, Black) to the contact section.

#### Scenario: View styled contact section
- **WHEN** user views the contact section
- **THEN** contact links use colors from the Blue, White, Grey, Black palette
- **AND** all links are clearly visible and styled consistently

### Requirement: External Link Handling
The system SHALL use the url_launcher package to handle external link navigation.

#### Scenario: Launch external link
- **WHEN** user clicks on any external contact link (GitHub or LinkedIn)
- **THEN** system uses url_launcher to open the URL
- **AND** link opens in a new browser tab or window

### Requirement: Contact Link Visibility
The system SHALL ensure all contact links are clearly visible with appropriate styling and spacing.

#### Scenario: Inspect contact links
- **WHEN** user inspects the contact section
- **THEN** all three contact links are visible
- **AND** links have appropriate spacing between them
- **AND** links are clearly distinguishable from one another

### Requirement: Console Error Handling
The system SHALL display the contact section without console errors.

#### Scenario: Load page with contact section
- **WHEN** the page loads with the contact section
- **THEN** contact section renders successfully
- **AND** no console errors are displayed
