## 1. Add SEO meta tags to web/index.html

- [ ] 1.1 Read CV.md Section 1 to extract professional description
- [ ] 1.2 Edit web/index.html to add `<title>Loh Zi Jian - Software Engineer</title>`
- [ ] 1.3 Edit web/index.html to add `<meta name="description">` tag with professional description
- [ ] 1.4 Edit web/index.html to add `<meta name="keywords" content="Flutter, Python, Java, Full-Stack Developer">`

## 2. Create sitemap.xml

- [ ] 2.1 Create web/sitemap.xml with valid XML structure
- [ ] 2.2 Add placeholder domain yourdomain.com in sitemap
- [ ] 2.3 List website routes in sitemap (home, about, projects, contact sections)

## 3. Create robots.txt

- [ ] 3.1 Create web/robots.txt with permissive settings
- [ ] 3.2 Add "User-agent: *" and "Allow: /" directives

## 4. Verification

- [ ] 4.1 Run `flutter run -d chrome` to verify browser title displays correctly
- [ ] 4.2 Inspect page source via browser dev tools to verify meta tags are present
- [ ] 4.3 Navigate to /sitemap.xml in browser to verify accessibility
- [ ] 4.4 Navigate to /robots.txt in browser to verify accessibility
- [ ] 4.5 Check browser console for any errors

## 5. Deployment preparation

- [ ] 5.1 Replace yourdomain.com placeholder with actual domain in sitemap.xml
