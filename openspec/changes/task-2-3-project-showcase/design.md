## Context

The personal resume website is a Flutter web-only application being built for hosting on a home server. Task 2.3 creates a project showcase section displaying 3 featured projects with cards. The site uses a minimalist color palette (Blue, White, Grey, Black) and requires responsive design with smooth scrolling integration into the single-page layout.

## Goals / Non-Goals

**Goals:**
- Create a project section widget that displays 3 featured projects with consistent card layout
- Load project images from assets directory using Image.asset()
- Display project details: description, tech stack, and measurable impact
- Add clickable link buttons for each project using url_launcher package
- Implement responsive layout: 2-3 column grid on desktop, single column on mobile
- Apply consistent styling matching the overall site theme

**Non-Goals:**
- Dynamic project data loading (hardcoded project data is acceptable)
- Project filtering or sorting
- Interactive project previews or modals
- Backend integration for project data

## Decisions

**Card Layout with Image Header**
- Projects displayed as vertical cards with image at top, content below
- Images sized consistently (e.g., 200px height with BoxFit.cover)
- Content includes: project name, description, tech stack badges, impact text, link button
- Cards have subtle shadow and rounded corners for depth

**Responsive Grid System**
- Desktop (>= 600px): Use GridView with 2-3 columns based on available width
- Mobile (< 600px): Single column layout using Column widget
- Consistent padding and spacing across breakpoints
- Media queries detected via MediaQuery.of(context).size.width

**Tech Stack Display**
- Display as chip/badge widgets with colored backgrounds
- Stack: Flutter, Janus WebRTC, Python, Django, GCP, NodeJS, Puppeteer, Docker
- Wrap with Wrap widget for flexible layout

**External Links**
- Use url_launcher package for opening URLs in new tabs
- Placeholder URLs initially, to be replaced with real links when available
- Link button styled as outlined or filled button matching theme

**Asset Loading**
- Use Image.asset() with error handling (errorBuilder)
- Provide fallback placeholder if image fails to load
- Assets declared in pubspec.yaml under flutter/assets section

## Risks / Trade-offs

**Image Loading Failures** → Implement errorBuilder to show placeholder UI and log errors without breaking the layout

**Inconsistent Image Dimensions** → Use BoxFit.cover with fixed height containers and consistent aspect ratios

**Content Overflow** → Use Flexible/Expanded widgets with text overflow handling (ellipsis for long descriptions)

**Placeholder URLs** → Keep buttons visible but disabled or with clear indicator that link is pending

**Cross-Browser Compatibility** → Test on Chrome, Firefox, Safari; use standard Flutter widgets for consistency
