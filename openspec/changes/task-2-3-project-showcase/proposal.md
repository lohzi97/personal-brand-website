## Why

The personal resume website needs a dedicated project showcase section to demonstrate proof-of-work and full-stack development capabilities. This section displays 3 featured projects from the portfolio, providing hiring managers with concrete examples of past work, technical expertise, and measurable impact.

## What Changes

- Create `lib/pages/projects_section.dart` with project card widgets
- Display 3 featured projects from project-portfolio.md with images, descriptions, tech stacks, and impact metrics
- Add external link buttons for each project (using url_launcher)
- Apply minimalist color theme (Blue, White, Grey, Black)
- Implement responsive layout: 2-3 column grid on desktop, single column on mobile

## Capabilities

### New Capabilities
- `project-showcase`: Display featured projects in a card-based layout with images, descriptions, tech stacks, and external links

### Modified Capabilities
- None

## Impact

- New file: `lib/pages/projects_section.dart`
- New dependencies: `url_launcher` package for external links
- Asset usage: `assets/ddone-google-play.jpeg`, `assets/ddone-microsoftstore.png`, `assets/cammillion-goals.png`, `assets/cammillion-srifactors.png`
- Integration: Will be included in `lib/main.dart` single-page layout (Task 2.6)
- No breaking changes to existing code
