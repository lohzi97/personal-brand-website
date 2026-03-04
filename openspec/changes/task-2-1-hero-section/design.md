## Context

The hero section is the first visual component visitors encounter on the personal brand website. It needs to quickly establish professional identity, convey the core value proposition, and provide easy access to downloadable credentials. The component will be built using Flutter for web deployment, following the minimalist aesthetic defined in the PRD (Simple Blue, White, Grey, Black).

Current state: Flutter web project structure exists with assets folder containing profile.png and CV.pdf. The `url_launcher` package needs to be added to handle the CV download functionality.

## Goals / Non-Goals

**Goals:**

- Create a visually appealing hero section that displays profile photo, title, bio, and CV download button
- Implement responsive layout that works on desktop and mobile viewports
- Apply the minimalist color palette (Blue, White, Grey, Black) consistently
- Ensure CV download button triggers browser download of `assets/CV.pdf`
- Create reusable Flutter component that can be easily integrated into main app layout

**Non-Goals:**

- Complex animations or transitions (keep it simple and fast-loading)
- Interactive profile photo features
- Multiple CV download options or language variants
- Social media sharing buttons (those are in the contact/footer section)

## Decisions

**Layout Structure:**

Use a `Column` widget with vertical layout to stack profile photo, title, bio text, and CV download button. Center align all content using `MainAxisAlignment.center` and `CrossAxisAlignment.center`. Wrap the Column in a `Container` with padding to provide spacing from viewport edges.

**Profile Image:**

Use `Image.asset('assets/profile.png')` with `BoxFit.cover` to ensure proper sizing. Wrap in a `ClipOval` widget for circular appearance (standard for professional profile photos). Set fixed dimensions (e.g., 150x150px) for consistency across devices.

**Typography:**

Title: Use `Text` widget with `TextStyle` featuring larger font size (e.g., 24-32px), bold weight (`FontWeight.bold`), and Blue color for emphasis.

Bio: Use `Text` widget with `TextStyle` featuring medium font size (e.g., 14-16px), normal weight, and Grey or Black color. Use `TextAlign.center` for better readability on wider screens.

**CV Download Button:**

Use `ElevatedButton` with Blue background and White text. OnPressed handler calls `url_launcher.launchUrl()` to trigger browser download of `assets/CV.pdf`. Button label: "Download CV".

**Color Palette:**

- Blue: Primary accent color for title and button (use Flutter's `Colors.blue` or custom hex value from PRD)
- White: Background color and button text color
- Grey: Secondary text color for bio
- Black: Optional for high-contrast text elements

**Responsive Design:**

Use `LayoutBuilder` to detect available width. On desktop (>600px), use horizontal spacing between profile photo and text elements (Row with Expanded). On mobile (<600px), use vertical stacking (Column). This aligns with PRD breakpoint at 600px.

**Asset Loading:**

Profile photo and CV.pdf must be declared in `pubspec.yaml` under `flutter: assets:` section. Use `Image.asset()` constructor which handles asset loading automatically. Add error handling with `errorBuilder` to display fallback if image fails to load.

## Risks / Trade-offs

**Risk:** Profile image may not load if file path is incorrect or asset not declared in pubspec.yaml
**Mitigation:** Add `errorBuilder` to `Image.asset` widget to display fallback placeholder or text

**Risk:** CV download may fail if asset path is wrong or `url_launcher` not properly configured
**Mitigation:** Verify asset path in `launchUrl()` call and add try-catch error handling with user feedback (e.g., SnackBar message)

**Trade-off:** Using `Image.asset()` requires rebuilding app when images change (vs. network images)
**Rationale:** Assets are static and rarely changed for this use case; local loading is faster and more reliable

**Trade-off:** Circular profile photo (ClipOval) may crop important details on some images
**Rationale:** Circular avatar is industry standard for professional profiles; user should provide appropriately cropped image
