## Why

The Flutter web project requires assets (images, fonts, CV PDF) to be properly declared in pubspec.yaml before they can be accessed in the code. Without this configuration, attempts to load assets will result in runtime errors, blocking development of the UI components that depend on these assets.

## What Changes

- Add Material Design flag and assets declaration to pubspec.yaml
- Declare assets/ directory as a valid asset location
- Run flutter pub get to install dependencies and process asset declarations
- Enable the Flutter app to load CV PDF, profile photo, and project images

## Capabilities

### New Capabilities

- `asset-configuration`: Configure pubspec.yaml to declare and enable Flutter asset loading for images, fonts, and PDF files

### Modified Capabilities

None

## Impact

- Modified: pubspec.yaml configuration
- Dependencies: flutter pub get will process new asset declarations
- Development workflow: Enables asset-based development for UI components
