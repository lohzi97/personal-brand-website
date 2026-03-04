## Context

The personal brand website is a Flutter Web application. Currently, the `web/index.html` file lacks proper SEO meta tags and no sitemap or robots.txt files exist. This limits search engine optimization capabilities and social media sharing optimization.

Current Flutter Web configuration:
- Build output directory: `build/web/`
- Source HTML template: `web/index.html`
- Client-side rendering by default (SEO limitations)

## Goals / Non-Goals

**Goals:**
- Add static SEO meta tags to improve search engine indexing
- Create sitemap.xml for search engine crawlers
- Create robots.txt to control crawler access
- Ensure proper page title and description for social media sharing

**Non-Goals:**
- Dynamic meta tag updates (beyond Flutter Web CSR limitations)
- Server-side rendering or pre-rendering implementation
- Advanced SEO features (structured data, Open Graph tags beyond basics)

## Decisions

**Static meta tags in web/index.html**
- Add `<title>`, `<meta name="description">`, and `<meta name="keywords">` tags directly to the HTML template
- Rationale: Flutter Web is client-side rendered, so meta tags must be set in the initial HTML file
- Alternative considered: Use flutter_seo package - rejected as overkill for basic SEO needs

**Placeholder domain in sitemap.xml**
- Use `yourdomain.com` as placeholder domain
- Rationale: Allows for easy domain replacement before deployment
- Alternative: Use localhost - rejected as not realistic for production sitemap

**Permissive robots.txt**
- Allow all crawlers (`User-agent: * Allow: /`)
- Rationale: Personal brand site should be fully indexable
- Alternative considered: Disallow specific paths - rejected as no sensitive routes exist

## Risks / Trade-offs

**CSR SEO limitations**
- [Risk] Search engines may not fully index content that requires JavaScript execution
- [Mitigation] Focus on static meta tags and proper HTML structure; document limitations

**Domain placeholder confusion**
- [Risk] Placeholder `yourdomain.com` may be forgotten during deployment
- [Mitigation] Add comment in sitemap.xml and include verification task in tasks.md

**Meta tag character limits**
- [Risk] Meta description may exceed optimal length (150-160 characters)
- [Mitigation] Ensure description from CV.md is concise and fits within limits
