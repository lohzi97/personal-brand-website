## 1. Setup

- [ ] 1.1 Verify url_launcher package is available in pubspec.yaml
- [ ] 1.2 Create lib/pages/experience_section.dart file

## 2. Core Widget Structure

- [ ] 2.1 Create ExperienceSection widget class extending StatelessWidget
- [ ] 2.2 Implement basic Column layout for vertical timeline
- [ ] 2.3 Add section title "Experience" with proper styling
- [ ] 2.4 Apply minimalist color palette (Blue, White, Grey, Black)

## 3. Role Display Components

- [ ] 3.1 Create _RoleCard helper widget for individual role entries
- [ ] 3.2 Implement company name display with color (Blue)
- [ ] 3.3 Implement date range display with color (Grey/Black)
- [ ] 3.4 Create bullet points list widget for achievements

## 4. Content Implementation

- [ ] 4.1 Add DotDash Technologies role (Jan 2025 - Present) with achievements from CV.md Section 2
- [ ] 4.2 Add Crea8 Capital / Celeropes role (Jan 2020 - Dec 2024) with achievements from CV.md Section 3
- [ ] 4.3 Add Freelance role (Ongoing) with achievements from CV.md Section 4
- [ ] 4.4 Ensure chronological order (DotDash first, then Crea8, then Freelance)

## 5. Company Website Links

- [ ] 5.1 Wrap company names in GestureDetector or InkWell
- [ ] 5.2 Implement url_launcher functionality for company links
- [ ] 5.3 Add placeholder URLs for company websites (e.g., "https://company-website.com")
- [ ] 5.4 Ensure links open in new browser tab

## 6. Styling and Layout

- [ ] 6.1 Apply proper padding and margins for role cards
- [ ] 6.2 Style bullet points with visual distinction (circle or standard bullet)
- [ ] 6.3 Ensure text is readable with appropriate font sizes
- [ ] 6.4 Add spacing between roles for visual separation

## 7. Responsive Design

- [ ] 7.1 Ensure full-width layout for Experience section
- [ ] 7.2 Test on desktop width (≥600px)
- [ ] 7.3 Test on mobile width (≤600px) with proper text wrapping
- [ ] 7.4 Verify no horizontal scrolling on any screen size

## 8. Testing and Validation

- [ ] 8.1 Run flutter run -d chrome and verify Experience section displays
- [ ] 8.2 Verify all 3 roles appear in correct chronological order
- [ ] 8.3 Test company links are clickable and open in new tab
- [ ] 8.4 Verify bullet points render correctly with proper formatting
- [ ] 8.5 Check for console errors or warnings
- [ ] 8.6 Verify content matches CV.md Sections 2-4

## 9. Integration

- [ ] 9.1 Import ExperienceSection in lib/main.dart
- [ ] 9.2 Add ExperienceSection to main page layout (after Projects, before Contact)
- [ ] 9.3 Test smooth scrolling to Experience section
- [ ] 9.4 Verify color theme consistency with other sections
