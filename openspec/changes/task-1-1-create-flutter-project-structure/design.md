## Context

This is a new project setup task to establish the Flutter web application foundation. The project currently has no codebase. All development (Hero, Competencies, Projects, Experience, Contact sections, reusable widgets) depends on this initial scaffolding being in place.

## Goals / Non-Goals

**Goals:**
- Create a working Flutter web-only project that can be launched in Chrome
- Establish the directory structure for future development (lib/widgets/, lib/pages/)
- Verify all required assets are present in the assets/ directory
- Configure the project for web-only deployment (no mobile/desktop)
- Enable hot reload development workflow with fvm

**Non-Goals:**
- Building any actual UI components or features (those are in subsequent tasks)
- Setting up CI/CD pipelines
- Configuring deployment infrastructure
- Setting up state management or other architectural layers

## Decisions

**Flutter Web-Only Platform**
- Use `flutter create --platforms web` to create a project that only supports the web platform
- Rationale: Reduces build artifacts and complexity by excluding mobile/desktop platforms that are not required per the PRD
- Alternative considered: Full Flutter project with all platforms - rejected as it adds unnecessary dependencies and build time

**Directory Structure: lib/widgets/ and lib/pages/**
- Create lib/widgets/ for reusable UI components that can be used across multiple sections
- Create lib/pages/ for section widgets (Hero, Competencies, Projects, Experience, Contact) as per PRD
- Rationale: Separation of concerns follows Flutter best practices and scales with future development
- Alternative considered: Flat structure in lib/ - rejected as it would become unmanageable with multiple sections

**FVM for Flutter Version Management**
- Use fvm to manage Flutter SDK version
- Rationale: Ensures consistent Flutter versions across development environments and prevents breaking changes
- Alternative considered: System-wide Flutter installation - rejected due to version consistency issues

**Asset Location: assets/ Directory**
- Place all assets (profile.png, CV.pdf, cammillion-goals.png, cammillion-srifactors.png, ddone-google-play.jpeg, ddone-microsoftstore.png) in the project root's assets/ directory
- Rationale: Standard Flutter convention, easy to reference in pubspec.yaml and code
- Alternative considered: Nested asset directories - rejected as unnecessary overhead for simple asset organization

**Entry Point: lib/main.dart**
- Use the default Flutter project structure with lib/main.dart as the application entry point
- Rationale: Standard Flutter convention, familiar to Flutter developers
- No alternative considered - this is the Flutter standard

## Risks / Trade-offs

**Risk: Flutter SDK version compatibility** → FVM mitigates by locking a specific Flutter version, preventing breaking changes from automatic updates

**Risk: Missing assets blocking development** → Verification step in acceptance criteria ensures all assets are present before proceeding; developers can add placeholder assets if actual files are not yet available

**Trade-off: Web-only platform limits future platform expansion** → Per PRD requirements, web-only is explicitly required; if mobile/desktop becomes needed later, re-running `flutter create --platforms android,ios,macos,windows,linux` would be needed

## Migration Plan

No migration needed - this is a new project from scratch.

Steps:
1. Run `flutter create --platforms web personal_resume_website`
2. Create lib/widgets/ directory
3. Create lib/pages/ directory
4. Verify assets/ directory contains all required files
5. Run `flutter run -d chrome` to verify project launches without errors
6. Commit the initialized project

Rollback strategy: Delete the project directory and start over if any step fails.

## Open Questions

None - all requirements are clear and standard Flutter setup procedures apply.
