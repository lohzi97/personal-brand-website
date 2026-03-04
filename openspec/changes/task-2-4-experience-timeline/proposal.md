## Why

The Experience Timeline section is a core component of the personal resume website, essential for demonstrating professional growth to hiring managers and technical recruiters. This change will display work experience chronologically with measurable impact metrics, which is critical for credibility and proving value as a full-stack developer.

## What Changes

- Add new `ExperienceTimeline` Flutter widget component to display professional experience in chronological order
- Create `lib/pages/experience_section.dart` with three role entries:
  - DotDash Technologies (Jan 2025 - Present)
  - Crea8 Capital / Celeropes (Jan 2020 - Dec 2024)
  - Freelance (Ongoing)
- Integrate with existing `url_launcher` package for clickable company website links
- Apply minimalist color palette (Blue, White, Grey, Black) consistent with site design
- Ensure responsive layout for Experience section (full width)

## Capabilities

### New Capabilities
- `experience-timeline`: Chronological display of professional roles with company names, dates, descriptions, and bullet points of measurable impact

### Modified Capabilities
- (none - no existing spec-level requirement changes)

## Impact

- **Affected Code**: New file `lib/pages/experience_section.dart`
- **Dependencies**: `url_launcher` package (already in pubspec.yaml from Task 1.2)
- **Content Source**: `docs/CV.md` Sections 2-4 for role descriptions and achievements
- **Design System**: Must align with minimalist color palette defined in PRD
- **Layout**: Full-width section following Project Showcase, preceding Contact/Footer
