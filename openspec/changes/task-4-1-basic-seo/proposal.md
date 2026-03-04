## Why

The personal brand website currently lacks basic SEO optimization, making it difficult for search engines to properly index and display the site in search results. Implementing basic SEO meta tags and sitemap files will improve search engine visibility and ensure the site appears correctly when shared on social media platforms.

## What Changes

- Add `<title>` tag to `web/index.html` with value "Loh Zi Jian - Software Engineer"
- Add `<meta name="description">` tag to `web/index.html` with professional description from CV.md
- Add `<meta name="keywords">` tag to `web/index.html` with value "Flutter, Python, Java, Full-Stack Developer"
- Create `web/sitemap.xml` file listing website routes (placeholder with yourdomain.com)
- Create `web/robots.txt` file allowing search engine crawlers

## Capabilities

### New Capabilities
- `basic-seo`: Meta tags, sitemap, and robots.txt implementation for search engine optimization

### Modified Capabilities
(None)

## Impact

- Modified files: `web/index.html` (adds meta tags in `<head>` section)
- New files: `web/sitemap.xml`, `web/robots.txt`
- Dependencies: None (uses only standard HTML and XML files)
- Browser compatibility: All modern browsers
- Flutter Web build: No changes to Flutter code, only static web assets
