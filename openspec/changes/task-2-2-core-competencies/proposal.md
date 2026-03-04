## Why

The Core Competencies section provides a rapid-fire breakdown of technical skills to showcase versatility and expertise. Currently, the personal brand website displays a Hero section but lacks a structured presentation of skills, making it difficult for visitors to quickly assess technical capabilities. Adding this section below the Hero will immediately establish credibility and help visitors understand the full technology stack.

## What Changes

- Create new Flutter page component `lib/pages/competencies_section.dart`
- Add competencies section to the single-page website layout below Hero section
- Implement 4 skill categories with badge-style tags:
  - Languages: Python, Java, JavaScript, VBA, MATLAB, C, C++, C#
  - Frameworks: Django, Spring Boot, NodeJS, Flutter
  - Databases & Cloud: MySQL, Redis, SQLite, GCP, Firebase
  - DevOps & Tools: Docker, k8s, Jenkins, GlitchTip, n8n, Linux
- Apply minimalist color palette (Blue, White, Grey, Black)
- Implement responsive design with breakpoint at 600px (mobile vs desktop)
- Ensure smooth scrolling integration with existing page layout

## Capabilities

### New Capabilities
- `competencies-display`: Display technical skills in categorized badge-style tags with responsive layout and consistent styling using Flutter widgets

### Modified Capabilities

## Impact

- New file: `lib/pages/competencies_section.dart`
- No breaking changes to existing components
- Additional UI section will extend the single-page layout below Hero
- No external dependencies required (uses existing Flutter widgets)
- Integrates with existing color palette and design system
