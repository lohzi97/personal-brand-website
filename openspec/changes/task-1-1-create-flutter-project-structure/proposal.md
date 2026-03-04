## Why

This change establishes the foundational Flutter web project structure needed for the personal resume website. Without this base setup, no development can proceed on any features or UI components.

## What Changes

- Create a new Flutter web-only project using `flutter create --platforms web personal_resume_website`
- Create directory structure: `lib/widgets/` for reusable UI components and `lib/pages/` for section widgets
- Verify and ensure all required assets exist in `assets/` directory: profile.png, CV.pdf, cammillion-goals.png, cammillion-srifactors.png, ddone-google-play.jpeg, ddone-microsoftstore.png
- Configure project for web-only platform (no mobile or desktop deployment)
- Set up fvm for Flutter version management

## Capabilities

### New Capabilities

- `flutter-project-setup`: Initial project scaffolding and directory structure for the Flutter web application

### Modified Capabilities

None - this is a new project setup task.

## Impact

- Creates the foundational codebase structure for the entire project
- Enables subsequent development of UI components and features
- Establishes Flutter web development environment and tooling
- No existing code is affected since this is a new project
