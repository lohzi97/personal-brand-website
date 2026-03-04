## Context

The Experience Timeline section will be a new Flutter widget component that displays professional work experience chronologically. The site uses Flutter web-only platform with a minimalist color palette (Blue, White, Grey, Black). The `url_launcher` package is already configured in pubspec.yaml from Task 1.2. The Experience section will be positioned after Project Showcase and before Contact/Footer in the single-page layout.

Content is sourced from `docs/CV.md` Sections 2-4, which contain detailed achievements for three roles: DotDash Technologies, Crea8 Capital / Celeropes, and Freelance work.

## Goals / Non-Goals

**Goals:**
- Create a clean, chronological timeline of professional roles with measurable impact
- Display company names with clickable website links (placeholder URLs)
- Show 2-3 bullet points per role highlighting key achievements
- Apply minimalist design consistent with site color palette
- Ensure full-width responsive layout for Experience section
- Integrate seamlessly into the single-page scrollable layout

**Non-Goals:**
- No filtering or sorting of experience (hardcoded chronological order)
- No interactive features beyond company website links
- No dynamic content loading (static content from CV.md)
- No complex animations or transitions

## Decisions

**Widget Structure: Single ExperienceSection Widget**
- Choice: Create `ExperienceSection` widget in `lib/pages/experience_section.dart` as a self-contained component
- Rationale: Keeps experience logic isolated and reusable. Each role can be a separate method or helper widget within the component.

**Layout: Vertical Timeline with Bulleted Achievements**
- Choice: Use Column layout with each role as a separate section containing title row (company + date) and bullet points below
- Rationale: Traditional resume format that hiring managers expect. Simple, scannable, and easy to implement with Flutter's Column/Row widgets. Bullet points use Flutter's `Bullet` widget or custom circle + text.

**Company Website Links: url_launcher Package**
- Choice: Use `url_launcher` package (already in pubspec.yaml) with `launchUrl()` for external links
- Rationale: Provides cross-platform URL launching. Package is already configured, no new dependencies needed. Placeholder URLs (e.g., "https://example.com") for now.

**Color Palette: Consistent with PRD**
- Choice: Use Blue for company names/links, Black/Grey for text, White background
- Rationale: Matches site-wide minimalist design. Blue draws attention to company names and links, maintaining visual hierarchy.

**Content Extraction: Manual from CV.md**
- Choice: Manually extract and format achievements from CV.md Sections 2-4 into the widget code
- Rationale: CV.md is already structured with clear achievements per role. No need for automated parsing. Content is static and changes infrequently.

## Risks / Trade-offs

**[Risk] Long Achievement Text Truncation on Mobile**
- Mitigation: Use `Flexible` or `Expanded` widgets with text overflow handling (`TextOverflow.ellipsis` if needed). Test on mobile viewport (≤600px breakpoint).

**[Risk] Placeholder URLs May Appear Unprofessional**
- Mitigation: Use generic but plausible placeholder URLs (e.g., "https://company-website.com"). Document in code comments that these are placeholders to be replaced with actual URLs.

**[Trade-off] Hardcoded vs Dynamic Content**
- Acceptance: Content is hardcoded for now. This is acceptable for a personal resume where updates are infrequent. Future enhancement could move to YAML/JSON or CMS.
