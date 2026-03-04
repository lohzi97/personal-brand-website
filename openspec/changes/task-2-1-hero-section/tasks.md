## 1. Setup

- [ ] 1.1 Add `url_launcher` dependency to `pubspec.yaml`
- [ ] 1.2 Verify `assets/profile.png` exists in assets folder
- [ ] 1.3 Verify `assets/CV.pdf` exists in assets folder
- [ ] 1.4 Declare assets in `pubspec.yaml` under `flutter: assets:` section (include `assets/`, `assets/profile.png`, `assets/CV.pdf`)
- [ ] 1.5 Run `flutter pub get` to install dependencies

## 2. Hero Section Structure

- [ ] 2.1 Create `lib/pages/hero_section.dart` file
- [ ] 2.2 Create `HeroSection` StatelessWidget extending `StatelessWidget`
- [ ] 2.3 Add `build(BuildContext context)` method returning a `Column` widget
- [ ] 2.4 Wrap Column in `Container` with padding (e.g., `EdgeInsets.all(40)`)
- [ ] 2.5 Configure Column with `MainAxisAlignment.center` and `CrossAxisAlignment.center`
- [ ] 2.6 Import necessary Flutter widgets: `import 'package:flutter/material.dart';`

## 3. Profile Photo Implementation

- [ ] 3.1 Add `Image.asset('assets/profile.png')` widget with `BoxFit.cover`
- [ ] 3.2 Wrap image in `SizedBox` with fixed dimensions (150x150px)
- [ ] 3.3 Wrap Sizedbox in `ClipOval` widget for circular appearance
- [ ] 3.4 Add `errorBuilder` to Image.asset to handle loading failures (display Text widget "Profile image not available")
- [ ] 3.5 Add spacer below profile photo (e.g., `SizedBox(height: 20)`)

## 4. Title Implementation

- [ ] 4.1 Add `Text` widget for title with content "Software Engineer & Technical Problem Solver"
- [ ] 4.2 Configure title Text widget with `TextStyle` (fontSize: 28, fontWeight: FontWeight.bold, color: Colors.blue)
- [ ] 4.3 Add `textAlign: TextAlign.center` to title
- [ ] 4.4 Add spacer below title (e.g., `SizedBox(height: 16)`)

## 5. Bio Text Implementation

- [ ] 5.1 Add `Text` widget for bio with exact content from CV.md Section 1
- [ ] 5.2 Configure bio Text widget with `TextStyle` (fontSize: 15, fontWeight: FontWeight.normal, color: Colors.grey[700])
- [ ] 5.3 Add `textAlign: TextAlign.center` to bio
- [ ] 5.4 Wrap bio Text in `SizedBox` with `maxWidth: 600` for better readability on wider screens
- [ ] 5.5 Add spacer below bio (e.g., `SizedBox(height: 24)`)

## 6. CV Download Button Implementation

- [ ] 6.1 Import `url_launcher` package: `import 'package:url_launcher/url_launcher.dart';`
- [ ] 6.2 Add `ElevatedButton` widget with label "Download CV"
- [ ] 6.3 Configure ElevatedButton with `style: ElevatedButton.styleFrom(backgroundColor: Colors.blue)`
- [ ] 6.4 Set button text color to `Colors.white`
- [ ] 6.5 Implement `onPressed` handler with async function
- [ ] 6.6 In onPressed handler, use `launchUrl()` to launch `assets/CV.pdf`
- [ ] 6.7 Add try-catch block in onPressed handler to catch launch errors
- [ ] 6.8 On error, display SnackBar with message "Failed to download CV" using `ScaffoldMessenger`

## 7. Responsive Layout

- [ ] 7.1 Wrap entire Column content in `LayoutBuilder` widget
- [ ] 7.2 Get available width from `constraints.maxWidth` in builder callback
- [ ] 7.3 Add conditional logic: if `constraints.maxWidth > 600`, use horizontal layout with Row
- [ ] 7.4 For desktop layout (>600px): create Row with profile photo on left and Column (title, bio, button) on right using Expanded
- [ ] 7.5 For mobile layout (≤600px): keep existing vertical Column layout
- [ ] 7.6 Ensure all elements remain center-aligned in both layouts

## 8. Integration

- [ ] 8.1 Export `HeroSection` from `lib/pages/hero_section.dart`
- [ ] 8.2 Import `HeroSection` in `lib/main.dart` or appropriate parent widget
- [ ] 8.3 Add `HeroSection()` widget to the app's main layout (e.g., in home page or body of Scaffold)

## 9. Testing and Validation

- [ ] 9.1 Run `flutter run -d chrome` to launch the app in Chrome
- [ ] 9.2 Verify profile photo displays correctly and is circular
- [ ] 9.3 Verify title text is "Software Engineer & Technical Problem Solver" with correct styling
- [ ] 9.4 Verify bio text matches CV.md Section 1 content with correct styling
- [ ] 9.5 Verify CV download button displays with correct styling (Blue background, White text)
- [ ] 9.6 Click CV download button and verify browser downloads `assets/CV.pdf`
- [ ] 9.7 Test responsive layout: resize browser window and verify layout adapts at 600px breakpoint
- [ ] 9.8 Check browser console for errors (no errors should appear)
- [ ] 9.9 Test error handling: temporarily remove `assets/profile.png` and verify fallback displays without errors
