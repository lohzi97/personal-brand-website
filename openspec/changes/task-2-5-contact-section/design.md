## Context

The personal brand website is a Flutter web application following a minimalist design with a Blue, White, Grey, and Black color palette. It uses a single-page layout with smooth scrolling. The contact section will be positioned at the bottom of the page as a footer element. The application currently has no contact mechanism, limiting visitor engagement.

## Goals / Non-Goals

**Goals:**
- Create a contact section widget that displays three contact links (Email, GitHub, LinkedIn)
- Implement responsive design with vertical stacking on mobile screens
- Use url_launcher package for proper handling of mailto: and external links
- Apply consistent styling following the existing color palette
- Integrate seamlessly into the existing single-page layout

**Non-Goals:**
- Contact form implementation
- Social media integration beyond the three specified links
- Custom animations or interactions beyond smooth scrolling

## Decisions

**Flutter Widget Structure**
- Create `ContactSection` as a stateless widget
- Use `GestureDetector` or `InkWell` for touch feedback on mobile
- Wrap links in `UrlLauncher` for external navigation
- Decision: Use Container with Column/Row for flexible responsive layout
- Alternative considered: ListTile - rejected as too material-design focused

**Styling Approach**
- Use project's defined color palette (Blue, White, Grey, Black)
- Implement hover effects for desktop users
- Decision: Define colors as constants in contact_section.dart for maintainability
- Alternative considered: Theme.of(context) colors - rejected to ensure exact color matching

**Responsive Layout**
- Use LayoutBuilder to detect screen width
- Desktop (> 600px): Horizontal row layout with icons and labels
- Mobile (≤ 600px): Vertical column layout with stacked links
- Decision: Breakpoint at 600px for mobile/tablet distinction
- Alternative considered: MediaQuery - rejected for simplicity

**Link Handling**
- Email: Use `mailto:` protocol for email client launch
- GitHub/LinkedIn: Use https URLs for external browser navigation
- Decision: Use url_launcher package with await launchUrl() for consistency
- Alternative considered: html anchor tags - rejected as not idiomatic Flutter

**Positioning**
- Place ContactSection at bottom of main page widget tree
- Add padding and background color for visual separation
- Decision: Container with margin-top and background color
- Alternative considered: Drawer/Scaffold bottom - rejected for single-page architecture

## Risks / Trade-offs

**url_launcher Platform Support**
- Risk: url_launcher behavior varies across platforms (web vs mobile)
- Mitigation: Test on Chrome target as specified, verify mailto: opens default email client

**Email Client Compatibility**
- Risk: mailto: may not work on all browsers/devices
- Mitigation: Document expected behavior, fallback to copy email address if needed

**Link Visibility**
- Risk: Contact links may not be discoverable at page bottom
- Mitigation: Use clear icons and labels, consider adding "Contact" heading

**Responsive Breakpoint**
- Risk: Fixed 600px breakpoint may not suit all devices
- Mitigation: Use Material Design breakpoint constants if needed, monitor user feedback
