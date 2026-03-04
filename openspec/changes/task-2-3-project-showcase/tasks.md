## 1. Project Setup

- [ ] 1.1 Create lib/pages/projects_section.dart file
- [ ] 1.2 Add url_launcher dependency to pubspec.yaml
- [ ] 1.3 Run flutter pub get to install new dependency

## 2. Core Widget Implementation

- [ ] 2.1 Create ProjectCard widget class with image, title, description, tech stack, impact, and link button
- [ ] 2.2 Implement image loading with Image.asset() and error handling (errorBuilder with placeholder)
- [ ] 2.3 Create TechStackBadge widget for displaying tech stack items as styled chips
- [ ] 2.4 Implement link button functionality using url_launcher with placeholder URLs

## 3. Section Widget Structure

- [ ] 3.1 Create ProjectsSection widget as StatelessWidget
- [ ] 3.2 Define project data structure with 3 hardcoded projects (DDOne, Cammillion Trading Bot, Infrastructure Enhancement)
- [ ] 3.3 Map project data to ProjectCard widgets using ListView or GridView

## 4. Responsive Layout

- [ ] 4.1 Implement LayoutBuilder to detect screen width
- [ ] 4.2 Create desktop layout (>= 600px) using GridView with 2-3 columns
- [ ] 4.3 Create mobile layout (< 600px) using single Column
- [ ] 4.4 Apply consistent padding and spacing for both layouts

## 5. Styling and Theming

- [ ] 5.1 Apply minimalist color palette (Blue, White, Grey, Black) to all card elements
- [ ] 5.2 Style card container with rounded corners and subtle shadow
- [ ] 5.3 Configure image containers with BoxFit.cover and fixed height (200px)
- [ ] 5.4 Style tech stack badges with colored backgrounds and consistent sizing
- [ ] 5.5 Style link buttons with theme color and hover effects

## 6. Integration

- [ ] 6.1 Import projects_section.dart in lib/main.dart
- [ ] 6.2 Add ProjectsSection widget to single-page layout (position after Competencies, before Experience)
- [ ] 6.3 Ensure smooth scrolling to projects section works correctly

## 7. Testing

- [ ] 7.1 Run flutter run -d chrome and verify projects section loads without errors
- [ ] 7.2 Verify all 3 project cards display with correct content from project-portfolio.md
- [ ] 7.3 Verify all project images load without errors (check console for image loading errors)
- [ ] 7.4 Verify project cards have consistent layout and styling
- [ ] 7.5 Verify link buttons are visible and clickable (test placeholder URLs open)
- [ ] 7.6 Test responsive layout at 375px (mobile) - verify single column layout
- [ ] 7.7 Test responsive layout at 1920px (desktop) - verify 2-3 column grid
- [ ] 7.8 Verify no console errors across all tests
