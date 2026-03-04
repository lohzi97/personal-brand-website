## ADDED Requirements

### Requirement: Page title tag
The web/index.html file SHALL contain a `<title>` tag with the value "Loh Zi Jian - Software Engineer".

#### Scenario: Title tag exists in HTML
- **WHEN** the web/index.html file is opened
- **THEN** the file contains `<title>Loh Zi Jian - Software Engineer</title>`

### Requirement: Meta description tag
The web/index.html file SHALL contain a `<meta name="description">` tag with a professional description derived from CV.md Section 1.

#### Scenario: Meta description tag exists in HTML
- **WHEN** the web/index.html file is opened
- **THEN** the file contains `<meta name="description" content="[professional description from CV.md Section 1]">`

### Requirement: Meta keywords tag
The web/index.html file SHALL contain a `<meta name="keywords">` tag with the value "Flutter, Python, Java, Full-Stack Developer".

#### Scenario: Meta keywords tag exists in HTML
- **WHEN** the web/index.html file is opened
- **THEN** the file contains `<meta name="keywords" content="Flutter, Python, Java, Full-Stack Developer">`

### Requirement: Sitemap file
A sitemap.xml file SHALL be created in the web/ directory with placeholder domain yourdomain.com listing website routes.

#### Scenario: Sitemap file exists
- **WHEN** the web/sitemap.xml file is opened
- **THEN** the file contains valid XML with sitemap structure
- **AND** the file includes placeholder domain yourdomain.com

### Requirement: Robots file
A robots.txt file SHALL be created in the web/ directory allowing all search engine crawlers.

#### Scenario: Robots file exists with permissive settings
- **WHEN** the web/robots.txt file is opened
- **THEN** the file contains "User-agent: *" followed by "Allow: /"
- **AND** the file allows all crawlers to access the site

### Requirement: Browser title display
When the Flutter Web application is loaded in a browser, the browser tab SHALL display the title "Loh Zi Jian - Software Engineer".

#### Scenario: Browser title shows correctly
- **WHEN** the Flutter Web application is launched with `flutter run -d chrome`
- **THEN** the browser tab displays "Loh Zi Jian - Software Engineer" as the page title

### Requirement: Page source verification
The HTML source of the loaded page SHALL contain all added meta tags when inspected via browser dev tools.

#### Scenario: Page source contains meta tags
- **WHEN** the page is viewed in browser and source is inspected
- **THEN** the source contains the title tag
- **AND** the source contains the meta description tag
- **AND** the source contains the meta keywords tag

### Requirement: Sitemap accessibility
The sitemap.xml file SHALL be accessible via browser navigation at the `/sitemap.xml` path.

#### Scenario: Sitemap is accessible
- **WHEN** the Flutter Web application is running
- **THEN** navigating to `/sitemap.xml` serves the sitemap.xml file

### Requirement: Robots file accessibility
The robots.txt file SHALL be accessible via browser navigation at the `/robots.txt` path.

#### Scenario: Robots file is accessible
- **WHEN** the Flutter Web application is running
- **THEN** navigating to `/robots.txt` serves the robots.txt file

### Requirement: Console error-free
The Flutter Web application SHALL not generate any console errors after adding SEO meta tags.

#### Scenario: No console errors on page load
- **WHEN** the Flutter Web application is launched
- **THEN** the browser console contains no errors related to the added meta tags or files
