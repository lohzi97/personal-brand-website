## Context

The Flutter web project has been initialized but assets have not been declared in pubspec.yaml. Currently, any attempt to load assets (images, fonts, CV PDF) using AssetImage or Image.asset will fail at runtime with "Unable to load asset" errors. The assets/ directory exists with project assets, but Flutter is not configured to recognize it.

## Goals / Non-Goals

**Goals:**

- Configure Flutter to recognize and load assets from the assets/ directory
- Enable Material Design widgets with uses-material-design flag
- Prepare the project for asset-based UI development
- Ensure flutter pub get processes the asset declarations successfully

**Non-Goals:**

- Implementing asset loading in Flutter code (handled by subsequent tasks)
- Adding specific asset files beyond the existing assets/ directory
- Asset optimization or caching strategies

## Decisions

**Declare entire assets/ directory rather than individual files**

- Rationale: Simpler maintenance, future-proof for adding new assets, less verbose configuration
- Alternative: Declare each file individually (assets/cv.pdf, assets/profile_photo.jpg, etc.)
- Trade-off: Directory declaration includes all files; individual declaration provides explicit control

**Use Material Design flag**

- Rationale: Project requires Material Design widgets for UI components
- No alternative considered; Material Design is standard for Flutter apps

## Risks / Trade-offs

- [Risk] Directory declaration may include unintended files if development artifacts are placed in assets/
  - Mitigation: Establish convention to keep assets/ directory clean with only production assets

- [Risk] Asset path errors if Flutter code uses incorrect paths
  - Mitigation: Follow PRD guidance for asset paths (assets/cv.pdf, assets/profile_photo.jpg)

- [Risk] Hot reload may not work if assets are not properly configured
  - Mitigation: Test hot reload after configuration as specified in acceptance criteria
