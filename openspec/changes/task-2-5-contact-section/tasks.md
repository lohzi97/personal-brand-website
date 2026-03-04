## 1. Setup and Dependencies

- [ ] 1.1 Add url_launcher package to pubspec.yaml
- [ ] 1.2 Run flutter pub get to install dependencies

## 2. Contact Section Widget Implementation

- [ ] 2.1 Create lib/pages/contact_section.dart file
- [ ] 2.2 Implement ContactSection as a StatelessWidget
- [ ] 2.3 Define color constants (Blue, White, Grey, Black) in contact_section.dart
- [ ] 2.4 Create ContactLink widget for individual link display
- [ ] 2.5 Implement responsive layout using LayoutBuilder with 600px breakpoint
- [ ] 2.6 Add horizontal row layout for desktop screens (> 600px)
- [ ] 2.7 Add vertical column layout for mobile screens (≤ 600px)
- [ ] 2.8 Add appropriate padding and spacing between links

## 3. Link Implementation

- [ ] 3.1 Implement Email link with mailto:lohzian@live.com
- [ ] 3.2 Implement GitHub link pointing to https://github.com/lohzi97
- [ ] 3.3 Implement LinkedIn link pointing to https://www.linkedin.com/in/loh-zi-jian/
- [ ] 3.4 Add url_launcher integration for external links (GitHub, LinkedIn)
- [ ] 3.5 Add url_launcher integration for mailto: link (Email)
- [ ] 3.6 Implement touch feedback using InkWell for mobile
- [ ] 3.7 Add hover effects for desktop users

## 4. Styling

- [ ] 4.1 Apply Blue, White, Grey, Black color palette to contact section
- [ ] 4.2 Style background color for footer area
- [ ] 4.3 Ensure all links are clearly visible with appropriate contrast
- [ ] 4.4 Add margin-top for visual separation from content above
- [ ] 4.5 Style link text to be clearly distinguishable

## 5. Integration

- [ ] 5.1 Integrate ContactSection into main page widget tree
- [ ] 5.2 Position ContactSection at bottom of page as footer
- [ ] 5.3 Ensure ContactSection appears after all other page content
- [ ] 5.4 Add "Contact" heading for discoverability

## 6. Testing and Validation

- [ ] 6.1 Run flutter run -d chrome to launch application
- [ ] 6.2 Verify contact section displays at bottom of page
- [ ] 6.3 Test email link opens default email client
- [ ] 6.4 Test GitHub link opens correct GitHub profile in new tab
- [ ] 6.5 Test LinkedIn link opens correct LinkedIn profile in new tab
- [ ] 6.6 Verify horizontal layout on desktop screen (> 600px)
- [ ] 6.7 Verify vertical layout on mobile screen (≤ 600px)
- [ ] 6.8 Check browser console for errors (should be none)
- [ ] 6.9 Verify all links are clearly visible and properly styled
