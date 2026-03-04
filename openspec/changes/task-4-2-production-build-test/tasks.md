## 1. Build Production Release

- [ ] 1.1 Run `flutter build web --release` to generate production build
- [ ] 1.2 Verify `build/web/` directory contains compiled files
- [ ] 1.3 Confirm build completes without errors

## 2. Serve Production Build Locally

- [ ] 2.1 Navigate to `build/web/` directory
- [ ] 2.2 Start Python HTTP server: `python -m http.server 8000`
- [ ] 2.3 Verify server starts successfully on port 8000

## 3. Verify Site Loads and Sections Render

- [ ] 3.1 Navigate browser to `http://localhost:8000`
- [ ] 3.2 Verify Hero section displays with name and tagline
- [ ] 3.3 Verify About section displays with bio content
- [ ] 3.4 Verify Skills section displays with skills list
- [ ] 3.5 Verify Projects section displays with project cards
- [ ] 3.6 Verify Contact section displays with contact links

## 4. Test External Links

- [ ] 4.1 Test CV download link - verify PDF downloads
- [ ] 4.2 Test GitHub link - verify profile opens in new tab
- [ ] 4.3 Test LinkedIn link - verify profile opens in new tab
- [ ] 4.4 Test email link - verify email client opens

## 5. Test Responsive Behavior

- [ ] 5.1 Set browser viewport to 375px (mobile)
- [ ] 5.2 Verify all sections stack vertically
- [ ] 5.3 Verify text is readable with no horizontal scroll
- [ ] 5.4 Set browser viewport to 1920px (desktop)
- [ ] 5.5 Verify desktop layout displays correctly with no overflow

## 6. Check for Console Errors

- [ ] 6.1 Open browser DevTools console
- [ ] 6.2 Verify no error-level messages appear
- [ ] 6.3 Verify no JavaScript runtime errors

## 7. Cleanup

- [ ] 7.1 Stop Python HTTP server
- [ ] 7.2 Verify all acceptance criteria are met
