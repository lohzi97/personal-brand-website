## Product Requirements Document: Personal Resume Website (Refined)

### 1. Product Vision & Objective
To build a highly responsive, resume-style personal website that acts as a digital portfolio for hiring managers and technical recruiters. The site will clearly demonstrate full-stack development capabilities, showcasing the ability to architect and deploy end-to-end solutions independently, while remaining approachable and collaborative for team environments.

### 2. Target Audience
- **Primary:** Hiring managers, technical recruiters, and CTOs looking for versatile full-stack developers and IT administrators
- **Secondary:** Potential collaborators for technical projects or freelance clients

### 3. Design & UI/UX Specifications
The visual identity must strike a balance between high-tech competence and an approachable personality.

- **Aesthetic Vibe:** IT and AI-focused, utilizing a "cute and minimalist" design language to convey friendliness and ease of communication
- **Color Palette:** Strictly Simple Blue, White, Grey, and Black
- **Anti-Goals:** No neon, glowing, or dark-web "cyberpunk" aesthetics
- **Typography:** Clean, highly readable sans-serif fonts suitable for a professional resume format
- **Layout:** Scannable, modular sections that allow a busy hiring manager to grasp core competencies within seconds
- **Accessibility:** Not a priority for this project

### 4. Technical Stack & Infrastructure

- **Frontend Framework:** Flutter web-only platform. No mobile or desktop deployment required. Standard build output (HTML/Canvas renderer).
- **Hosting & Deployment:** Self-hosted on local home server (basic machine with 2-4GB RAM)
- **Web Server:** Nginx running in Docker container for easy management on Linux environment
- **Domain & Security:** Custom domain (to be acquired via Namecheap) routing through Cloudflare with Cloudflare's own SSL/TLS certificates (Origin Certificate) for secure HTTPS access. For development, use localhost.
- **Deployment Method:** Manual deployment - build locally, transfer via rsync/SCP to server, restart Docker container manually
- **Backup Strategy:** Git-based version control for code and server configuration (Docker Compose files, Nginx configuration).
- **Analytics:** None (no visitor tracking)

#### Development Environment Requirements
- **Flutter SDK:** Managed via fvm (Flutter Version Management) - web-only platform required
- **Dart SDK:** Included with Flutter (via fvm)
- **IDE:** VS Code with Flutter extension or Android Studio
- **Git:** For version control
- **Docker:** For containerized Nginx deployment (optional for local testing)

#### Flutter Web Renderers
Flutter Web offers multiple rendering options. For this project:
- **Default (CanvasKit):** High-performance Canvas renderer using WebGL. Best for most use cases, provides consistent rendering across browsers.
- **HTML Renderer:** Uses HTML/CSS elements instead of Canvas. Better for older browsers, text-heavy content, or when you need better accessibility support.
- **skwasm (WebAssembly):** Experimental renderer with WasmGC support. Offers better performance but requires modern browsers.

**Recommendation:** Use default CanvasKit renderer for best performance and consistency. Switch to HTML renderer if you encounter compatibility issues on older browsers.

#### Docker Configuration
- **Docker Compose:** Used to orchestrate Nginx container
- **Nginx Config:** Serves static Flutter web build artifacts from `/usr/share/nginx/html`
- **SSL/TLS:** Cloudflare Origin Certificate (obtained from Cloudflare dashboard) configured in Nginx
- **No Certificate Renewal Needed:** Cloudflare SSL certificates have longer validity and can be manually updated

### 5. Core Features & Architecture (MVP)

| Section | Description | Key Elements |
| --- | --- | --- |
| **Hero/Header** | A welcoming introduction that establishes identity and profession | Friendly profile photo/avatar (ready in assets folder), clear title \"Full-Stack Developer & Systems Admin\", and a primary \"Download CV\" button |
| **Core Competencies** | A rapid-fire breakdown of technical skills to prove versatility | Text badges/tags grouped by category for Frontend (Flutter, JS), Backend (Node.js, Python, Java), Infrastructure (Kubernetes, Docker, Linux), and AI integrations |
| **Project Showcase** | The core proof-of-work section demonstrating the \"can build almost anything\" capability. **3 featured projects:**<br>1. **DDOne (VoIP PBX)** - Cross-platform app (Android/iOS/Windows/MacOS), resolved critical stability issues, passed Google/Microsoft/Apple review processes<br>2. **Cammillion Trading Bot** - Python/Django, Redis, Docker, 24/7 operations on GCP, executes trades across stocks/futures/forex<br>3. **Infrastructure Enhancement** - Reduced GCP storage costs by 50% by migrating to cloud buckets, integrated Telegram reporting for scraping alerts | Full breakdown per project: description, tech stack, problem solved, measurable impact, and available links (demo OR code, whichever exists) |
| **Experience Timeline** | A traditional, clean chronological view of professional roles | Company names, dates (with website links), brief role description, and 2-3 bullet points of measurable impact per role |
| **Contact/Footer** | A frictionless way for hiring managers to reach out | Direct email link (mailto:), LinkedIn profile link, GitHub repository link (no contact form) |
| **CV Download** | Hosted PDF file for easy downloading | Static PDF at `assets/cv.pdf`, served from web server, downloadable via button/link |

### 6. SEO Requirements
**Note:** Flutter Web is client-side rendered by default, which limits SEO capabilities. This project accepts limited SEO for now with a plan to improve later (e.g., SSG/SSR).

**Client-Side Rendering Implications:**
- Initial page load may show blank or loading state to search engine crawlers
- Content is not indexable until JavaScript executes
- Meta tags need to be set in `web/index.html` (cannot be dynamically updated after initial load)
- Some crawlers may struggle with SPA routing

- **Basic SEO Implementation** (manual approach):
  - Edit `web/index.html` to add meta tags:
    - `<title>` tag for page title
    - `<meta name="description">` for page description
    - `<meta name="keywords">` for keywords
    - Open Graph tags for social media sharing
  - Create static `sitemap.xml` file listing all routes/sections
  - Create static `robots.txt` allowing search engine crawlers (`User-agent: * Allow: /`)
- **Heading Structure:** Use proper HTML heading tags (h1, h2, h3) in Flutter widgets (via `Semantics` or HTML widget wrappers)
- **Future Enhancement:** Consider packages like `meta_seo` for dynamic meta tag updates when expanding SEO

### 7. Content Management
- Manual code updates for all content changes
- Content to be generated based on project portfolio documentation
- Existing images available in assets folder (use existing formats as-is)
- **Asset Management:**
  - Declare all assets (images, fonts, CV PDF) in `pubspec.yaml` under `assets:` section
  - Example `pubspec.yaml` configuration:
    ```yaml
    flutter:
      uses-material-design: true
      assets:
        - assets/
        - assets/cv.pdf
        - assets/profile_photo.jpg
        - assets/projects/
    ```
  - Use `AssetImage` or `Image.asset()` widgets to reference assets in Flutter code
  - CV PDF path: `assets/cv.pdf`
  - Profile photo and project images in `assets/` directory
  - Update frequency: Rarely (quarterly/yearly) - only when major portfolio or experience changes occur

### 8. Development Milestones

1. **Phase 1: Wireframing & Content Preparation**
   - Define the exact layout and sections
   - Generate bio text based on project portfolio
   - Prepare CV PDF
   - Organize project screenshots and assets

2. **Phase 2: Flutter Development**
    - Set up Flutter project structure (web-only platform):
      - Create project: `flutter create --platforms web personal_resume_website`
      - `lib/main.dart` - entry point
      - `lib/widgets/` - reusable UI components
      - `lib/pages/` - section widgets (Hero, Competencies, Projects, Experience, Contact)
      - `assets/` - images, fonts, CV PDF
      - `web/index.html` - HTML template with SEO meta tags
      - `pubspec.yaml` - dependencies and asset declarations
   - Declare assets in `pubspec.yaml` under `assets:` section
   - Build the UI components for all sections using `AssetImage` or `Image.asset()` for images
   - Implement single-page layout with smooth scrolling
   - Apply the minimalist color palette (Blue, White, Grey, Black)
   - Implement CV download functionality (hosted PDF at `assets/cv.pdf`)
   - Add direct contact links (email mailto:, LinkedIn, GitHub)
   - Ensure mobile responsiveness:
     - Use `LayoutBuilder` and `MediaQuery` for adaptive layouts
     - Define breakpoint at 600px for mobile vs desktop
     - Use `Row`/`Column` with `Expanded`/`Flexible` widgets
     - Single layout that adapts across screen sizes
   - Implement basic SEO:
     - Edit `web/index.html` to add title, meta description, keywords
     - Create static `sitemap.xml` file
     - Create static `robots.txt` allowing search engine crawlers
    - Local testing workflow:
      - Use `fvm flutter run -d chrome` for local development with hot reload
      - Use `fvm flutter build web --release` for production build
      - Test production build locally: serve `build/web/` directory with simple HTTP server (e.g., `python -m http.server 8000` or `npx serve`)
      - Test on multiple browsers (Chrome, Safari, Firefox)
      - Test mobile responsiveness using browser dev tools
      - Verify SPA routing works correctly (navigate to different sections without page refresh)

3. **Phase 3: Server Provisioning**
    - Configure the home server environment (basic machine)
    - Install Docker and Docker Compose
    - Create Dockerfile for Nginx container:
      ```
      FROM nginx:alpine
      COPY nginx.conf /etc/nginx/conf.d/default.conf
      COPY build/web/ /usr/share/nginx/html
      RUN chmod -R 755 /usr/share/nginx/html
      ```
    - Create Nginx configuration (`nginx.conf`):
      ```nginx
      server {
          listen 80;
          server_name yourdomain.com www.yourdomain.com;

          root /usr/share/nginx/html;
          index index.html;

          # Handle SPA routing - all routes serve index.html
          location / {
              try_files $uri $uri/ /index.html;
          }

          # Cache static assets
          location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|wasm|dat|json)$ {
              expires 1y;
              add_header Cache-Control "public, immutable";
          }

          # Gzip compression
          gzip on;
          gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

          # Security headers
          add_header X-Frame-Options "SAMEORIGIN" always;
          add_header X-Content-Type-Options "nosniff" always;
      }

      # HTTPS server block (if using Cloudflare Origin Certificate)
      server {
          listen 443 ssl http2;
          server_name yourdomain.com www.yourdomain.com;

          root /usr/share/nginx/html;
          index index.html;

          ssl_certificate /etc/nginx/ssl/origin.crt;
          ssl_certificate_key /etc/nginx/ssl/origin.key;

          # Same routing and caching as HTTP
          location / {
              try_files $uri $uri/ /index.html;
          }

          location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|wasm|dat|json)$ {
              expires 1y;
              add_header Cache-Control "public, immutable";
          }

          gzip on;
          gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

          add_header X-Frame-Options "SAMEORIGIN" always;
          add_header X-Content-Type-Options "nosniff" always;
      }
      ```
    - Create `docker-compose.yml` to orchestrate Nginx container:
      ```yaml
      version: '3.8'
      services:
        nginx:
          build: .
          ports:
            - "80:80"
            - "443:443"
          restart: unless-stopped
      ```
    - Configure Cloudflare DNS to point custom domain to server IP
    - Enable proxy and SSL/TLS (Full) mode in Cloudflare
    - Generate Cloudflare Origin Certificate:
      - Go to Cloudflare SSL/TLS > Origin Server
      - Click "Create Certificate"
      - Download origin.crt and origin.key
      - Place in nginx config directory on server

4. **Phase 4: Testing & Launch**
   - Ensure cross-browser compatibility (Chrome, Safari, Firefox)
   - Verify mobile responsiveness of the Flutter web app
   - Test CV download functionality
   - Verify all contact links work correctly
   - Configure Nginx access and error logging
   - Set up log rotation to prevent disk space issues
   - Point domain to server and go live

5. **Phase 5: Deployment Process**
    - Build Flutter web app: `fvm flutter build web --release`
    - Output generated in `build/web/` directory
    - Transfer build artifacts to server: `rsync -avz build/web/ user@server:/path/to/nginx/html/`
    - Rebuild and restart Docker container: `docker-compose up -d --build`
    - Verify deployment: `curl https://yourdomain.com`
    - Update `sitemap.xml` and `robots.txt` if needed
    - Test SPA routing by navigating to different routes (e.g., /about, /projects)

### 9. Performance Requirements
- Basic functional performance
- No strict performance metrics (Core Web Vitals compliance not required)
- Focus on functionality over optimization

### 10. Monitoring & Maintenance
- **Server Logging:**
  - Enable Nginx access logs (`/var/log/nginx/access.log`)
  - Enable Nginx error logs (`/var/log/nginx/error.log`)
  - Set up log rotation to prevent disk space issues
- **Basic Monitoring:**
  - Use simple uptime monitoring (e.g., UptimeRobot)
  - Monitor SSL certificate expiration date
  - Check disk space usage on home server
- **Troubleshooting:**
  - Document common deployment issues and fixes
  - Keep record of Docker container health status
- **Backup Strategy:**
  - Git tracks all code and configuration files (Docker Compose, Nginx config)
  - Cloudflare Origin Certificate should be backed up securely (download and store safely)
  - Document server provisioning steps for disaster recovery

### 11. Timeline
- Flexible - no specific deadline
- Quality over speed approach
