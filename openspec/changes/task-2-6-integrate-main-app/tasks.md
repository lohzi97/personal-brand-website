## 1. Setup and Imports

- [ ] 1.1 Create backup of original `lib/main.dart`
- [ ] 1.2 Import Hero section widget in `lib/main.dart`
- [ ] 1.3 Import Competencies section widget in `lib/main.dart`
- [ ] 1.4 Import Projects section widget in `lib/main.dart`
- [ ] 1.5 Import Experience section widget in `lib/main.dart`
- [ ] 1.6 Import Contact section widget in `lib/main.dart`

## 2. Color Theme Definition

- [ ] 2.1 Define Blue color constant with appropriate hex value
- [ ] 2.2 Define White color constant with appropriate hex value
- [ ] 2.3 Define Grey color constant with appropriate hex value
- [ ] 2.4 Define Black color constant with appropriate hex value
- [ ] 2.5 Create `ThemeData` object with the color palette
- [ ] 2.6 Apply `ThemeData` to `MaterialApp` widget
- [ ] 2.7 Verify theme colors are accessible to child widgets

## 3. App Structure Implementation

- [ ] 3.1 Create `SingleChildScrollView` as root widget for vertical scrolling
- [ ] 3.2 Create `Column` widget inside `SingleChildScrollView` to hold sections
- [ ] 3.3 Add Hero section widget as first child of Column
- [ ] 3.4 Add Competencies section widget as second child of Column
- [ ] 3.5 Add Projects section widget as third child of Column
- [ ] 3.6 Add Experience section widget as fourth child of Column
- [ ] 3.7 Add Contact section widget as fifth child of Column
- [ ] 3.8 Verify sections render in correct order (Hero → Competencies → Projects → Experience → Contact)
- [ ] 3.9 Verify no unwanted gaps or overlaps between sections

## 4. Smooth Scrolling Configuration

- [ ] 4.1 Add `ScrollConfiguration` widget wrapping the scrollable content
- [ ] 4.2 Configure `AlwaysScrollableScrollPhysics` for consistent scroll behavior
- [ ] 4.3 Verify smooth scrolling works with mouse wheel
- [ ] 4.4 Verify smooth scrolling works with touch gestures
- [ ] 4.5 Verify scroll behavior is consistent across platforms

## 5. Responsive Layout Implementation

- [ ] 5.1 Add `LayoutBuilder` widget to detect screen constraints
- [ ] 5.2 Add `MediaQuery` usage to get screen dimensions
- [ ] 5.3 Implement 600px breakpoint logic for mobile vs desktop
- [ ] 5.4 Test mobile layout behavior below 600px width
- [ ] 5.5 Test desktop layout behavior at 600px or above
- [ ] 5.6 Verify no horizontal scrolling occurs on any screen size
- [ ] 5.7 Verify content fits within screen width on all devices

## 6. Section Widget Theme Integration

- [ ] 6.1 Review Hero section widget for hardcoded colors
- [ ] 6.2 Update Hero section to use theme colors where hardcoded
- [ ] 6.3 Review Competencies section widget for hardcoded colors
- [ ] 6.4 Update Competencies section to use theme colors where hardcoded
- [ ] 6.5 Review Projects section widget for hardcoded colors
- [ ] 6.6 Update Projects section to use theme colors where hardcoded
- [ ] 6.7 Review Experience section widget for hardcoded colors
- [ ] 6.8 Update Experience section to use theme colors where hardcoded
- [ ] 6.9 Review Contact section widget for hardcoded colors
- [ ] 6.10 Update Contact section to use theme colors where hardcoded

## 7. Testing and Validation

- [ ] 7.1 Run `flutter run -d chrome` to start the application
- [ ] 7.2 Verify full page loads with all sections visible
- [ ] 7.3 Test smooth scrolling between sections using mouse wheel
- [ ] 7.4 Test smooth scrolling between sections using touch gestures
- [ ] 7.5 Verify color theme is consistently Blue, White, Grey, Black across all sections
- [ ] 7.6 Test on mobile screen size (< 600px) and verify no horizontal scrolling
- [ ] 7.7 Test on desktop screen size (≥ 600px) and verify proper layout
- [ ] 7.8 Check browser console for any errors
- [ ] 7.9 Verify all acceptance criteria are met
