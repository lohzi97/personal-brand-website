## ADDED Requirements

### Requirement: Display project cards
The system SHALL display 3 featured projects in a card-based layout, each containing an image, project name, description, tech stack, impact metric, and external link button.

#### Scenario: Projects section loads
- **WHEN** user navigates to the projects section
- **THEN** system displays exactly 3 project cards in vertical order or grid layout
- **AND** each card contains all required elements (image, name, description, tech stack, impact, link)

#### Scenario: DDOne project card displays
- **WHEN** projects section renders
- **THEN** first card shows DDOne (VoIP PBX) with image from assets/ddone-google-play.jpeg or assets/ddone-microsoftstore.png
- **AND** card displays Flutter and Janus WebRTC tech stack badges
- **AND** card shows impact: "Public release on Google/Apple/Microsoft stores"

#### Scenario: Cammillion Trading Bot card displays
- **WHEN** projects section renders
- **THEN** second card shows Cammillion Trading Bot with image from assets/cammillion-goals.png or assets/cammillion-srifactors.png
- **AND** card displays Python, Django, GCP tech stack badges
- **AND** card shows impact: "24/7 operations on GCP"

#### Scenario: Infrastructure Enhancement card displays
- **WHEN** projects section renders
- **THEN** third card shows Infrastructure Enhancement with image from assets/cammillion-srifactors.png
- **AND** card displays NodeJS, Puppeteer, Docker tech stack badges
- **AND** card shows impact: "Reduced GCP storage costs by 50%"

### Requirement: Load project images from assets
The system SHALL load project images using Image.asset() with proper error handling and fallback display.

#### Scenario: Project image loads successfully
- **WHEN** project card renders and image asset is available
- **THEN** system displays the image at specified asset path without errors
- **AND** image is sized with BoxFit.cover and consistent height (200px)

#### Scenario: Project image fails to load
- **WHEN** project card renders and image asset is missing or corrupted
- **THEN** system displays placeholder UI (gray box or error icon) instead of breaking layout
- **AND** error is logged to console for debugging

### Requirement: Display tech stack as badges
The system SHALL display each project's tech stack as styled chip/badge widgets with text labels.

#### Scenario: Tech stack badges render
- **WHEN** project card displays
- **THEN** tech stack items render as badge widgets with colored backgrounds
- **AND** badges wrap to multiple lines if needed (using Wrap widget)
- **AND** badges have consistent styling across all project cards

### Requirement: Open external project links
The system SHALL open external project URLs in new browser tabs when link buttons are clicked.

#### Scenario: Link button clicked with valid URL
- **WHEN** user clicks project link button with valid URL
- **THEN** system opens the URL in new browser tab using url_launcher
- **AND** page remains on current website

#### Scenario: Link button clicked with placeholder URL
- **WHEN** user clicks project link button with placeholder URL
- **THEN** button is disabled or shows indicator that link is pending
- **OR** button opens placeholder URL in new tab with clear message

### Requirement: Responsive layout adaptation
The system SHALL adapt project card layout based on screen width: 2-3 column grid on desktop (>= 600px), single column on mobile (< 600px).

#### Scenario: Desktop layout renders
- **WHEN** screen width is >= 600px
- **THEN** project cards display in 2-3 column grid using GridView
- **AND** cards expand to fill available width with consistent spacing

#### Scenario: Mobile layout renders
- **WHEN** screen width is < 600px
- **THEN** project cards display in single column vertical layout
- **AND** each card occupies full width with consistent vertical spacing

### Requirement: Apply minimalist color theme
The system SHALL apply the site's color theme (Blue, White, Grey, Black) consistently to all project card elements.

#### Scenario: Card colors match theme
- **WHEN** project cards render
- **THEN** card backgrounds use White (#FFFFFF)
- **AND** text uses Black (#000000) or Grey (#808080) for secondary text
- **AND** accents (buttons, badges, borders) use Blue theme color
- **AND** no neon, glowing, or cyberpunk colors are used

### Requirement: Display project descriptions
The system SHALL display descriptive text for each project extracted from docs/project-portfolio.md.

#### Scenario: Project descriptions display
- **WHEN** project cards render
- **THEN** each card shows description text from corresponding section in project-portfolio.md
- **AND** text is readable with appropriate line height and spacing
- **AND** long descriptions truncate with ellipsis if needed
