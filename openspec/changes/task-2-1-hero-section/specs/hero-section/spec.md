## ADDED Requirements

### Requirement: Profile Photo Display
The system SHALL display a circular profile photo using the image from `assets/profile.png`.

#### Scenario: Profile photo loads successfully
- **WHEN** the hero section renders
- **THEN** the profile photo is displayed as a circular image
- **AND** the image dimensions are fixed at 150x150px
- **AND** the image uses `BoxFit.cover` for proper scaling

### Requirement: Professional Title Display
The system SHALL display the professional title "Software Engineer & Technical Problem Solver" in Blue color with bold font weight.

#### Scenario: Title renders with correct styling
- **WHEN** the hero section renders
- **THEN** the title text is "Software Engineer & Technical Problem Solver"
- **AND** the font size is between 24-32px
- **AND** the font weight is bold
- **AND** the color is Blue
- **AND** the text is center-aligned

### Requirement: Bio Text Display
The system SHALL display the bio text excerpt from CV.md Section 1: "I bridge the gap between complex code and real-world business results, ensuring that technology serves the bottom line, not the other way around."

#### Scenario: Bio renders with correct content and styling
- **WHEN** the hero section renders
- **THEN** the bio text matches the exact content from CV.md Section 1
- **AND** the font size is between 14-16px
- **AND** the font weight is normal
- **AND** the color is Grey or Black
- **AND** the text is center-aligned

### Requirement: CV Download Button
The system SHALL provide a "Download CV" button that triggers browser download of the CV PDF file located at `assets/CV.pdf`.

#### Scenario: User clicks CV download button
- **WHEN** user clicks the "Download CV" button
- **THEN** the browser downloads the file at `assets/CV.pdf`
- **AND** the download action completes without errors

#### Scenario: CV download button displays correctly
- **WHEN** the hero section renders
- **THEN** the button displays "Download CV" text
- **AND** the button background is Blue
- **AND** the button text is White
- **AND** the button is clickable

### Requirement: Layout Structure
The system SHALL arrange hero section elements in a vertically stacked column with center alignment.

#### Scenario: Desktop layout displays correctly
- **WHEN** viewport width is greater than 600px
- **THEN** profile photo and text elements are horizontally aligned (if using Row)
- **OR** profile photo and text elements are vertically stacked with appropriate spacing
- **AND** all elements are centered horizontally

#### Scenario: Mobile layout displays correctly
- **WHEN** viewport width is 600px or less
- **THEN** all elements are vertically stacked in a Column
- **AND** profile photo appears above title
- **AND** title appears above bio
- **AND** bio appears above CV download button
- **AND** all elements are centered horizontally

### Requirement: Color Palette Application
The system SHALL apply the minimalist color palette (Blue, White, Grey, Black) consistently across all hero section elements.

#### Scenario: Colors match design specification
- **WHEN** the hero section renders
- **THEN** title uses Blue color
- **AND** button uses Blue background with White text
- **AND** bio uses Grey or Black color
- **AND** background uses White color

### Requirement: Asset Loading Error Handling
The system SHALL display fallback content if profile photo fails to load.

#### Scenario: Profile photo fails to load
- **WHEN** the profile image at `assets/profile.png` cannot be loaded
- **THEN** a fallback placeholder or text is displayed
- **AND** the rest of the hero section continues to render normally
- **AND** no console errors are thrown for missing image

### Requirement: CV Download Error Handling
The system SHALL provide user feedback if CV download fails.

#### Scenario: CV download fails
- **WHEN** the CV download action encounters an error
- **THEN** an error message is displayed to the user
- **AND** the error message explains that the download failed
- **AND** no console errors are thrown
