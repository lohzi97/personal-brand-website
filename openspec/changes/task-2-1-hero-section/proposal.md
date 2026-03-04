## Why

The personal brand website requires a prominent hero section to establish identity, communicate professional positioning, and provide immediate access to downloadable credentials. This foundational component creates the first impression for hiring managers and serves as the entry point to the entire portfolio.

## What Changes

- Create new hero section component at `lib/pages/hero_section.dart`
- Display profile photo using `Image.asset('assets/profile.png')`
- Render title: "Software Engineer & Technical Problem Solver"
- Show bio excerpt from CV.md Section 1: "I bridge the gap between complex code and real-world business results, ensuring that technology serves the bottom line, not the other way around."
- Add CV download button that links to `assets/CV.pdf`
- Integrate `url_launcher` package to trigger CV download
- Apply minimalist color palette (Blue, White, Grey, Black)

## Capabilities

### New Capabilities

- `hero-section`: Core header component featuring profile image, professional title, bio text, and CV download functionality

### Modified Capabilities

None

## Impact

- New component file: `lib/pages/hero_section.dart`
- Asset dependencies: `assets/profile.png` and `assets/CV.pdf` must be declared in `pubspec.yaml`
- New Flutter dependency: `url_launcher` package required
- Integration point: Hero section will be called from main app layout
