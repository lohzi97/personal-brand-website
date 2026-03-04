## 1. Setup

- [ ] 1.1 Create `lib/pages/competencies_section.dart` file
- [ ] 1.2 Import required Flutter widgets and dependencies

## 2. Data Structure

- [ ] 2.1 Define Languages category data: Python, Java, JavaScript, VBA, MATLAB, C, C++, C#
- [ ] 2.2 Define Frameworks category data: Django, Spring Boot, NodeJS, Flutter
- [ ] 2.3 Define Databases & Cloud category data: MySQL, Redis, SQLite, GCP, Firebase
- [ ] 2.4 Define DevOps & Tools category data: Docker, k8s, Jenkins, GlitchTip, n8n, Linux

## 3. UI Components

- [ ] 3.1 Create SkillBadge widget with rounded corners and consistent styling
- [ ] 3.2 Create CategorySection widget for displaying category header and badges
- [ ] 3.3 Implement Wrap widget for badge layout to handle wrapping

## 4. Layout Implementation

- [ ] 4.1 Implement responsive layout using LayoutBuilder to detect screen width
- [ ] 4.2 Create desktop layout (>600px) with Row for 2x2 grid of categories
- [ ] 4.3 Create mobile layout (≤600px) with Column for stacked categories
- [ ] 4.4 Add appropriate spacing between categories using padding

## 5. Styling

- [ ] 5.1 Apply Blue color to category headers
- [ ] 5.2 Apply Grey or Black background with White text to badge tags
- [ ] 5.3 Set consistent padding and border radius for badge tags
- [ ] 5.4 Ensure all colors match minimalist palette (Blue, White, Grey, Black)

## 6. Integration

- [ ] 6.1 Import CompetenciesSection widget in main page file
- [ ] 6.2 Position competencies section below Hero section
- [ ] 6.3 Verify smooth scrolling from Hero to Competencies section

## 7. Testing

- [ ] 7.1 Run `flutter run -d chrome` to launch application
- [ ] 7.2 Verify competencies section displays below Hero section
- [ ] 7.3 Verify all 4 categories are displayed with correct skills
- [ ] 7.4 Verify all badges render correctly with proper spacing
- [ ] 7.5 Test responsive layout by resizing browser window around 600px breakpoint
- [ ] 7.6 Test hot reload by modifying badge styling and triggering hot reload
- [ ] 7.7 Verify no console errors appear in browser developer console
