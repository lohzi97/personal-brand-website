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

- **Frontend Framework:** Flutter (deployed as a web application). Standard build output.
- **Hosting & Deployment:** Self-hosted on local home server (basic machine with 2-4GB RAM)
- **Web Server:** Nginx or Apache (running on Linux environment) to serve the compiled Flutter web files, potentially containerized via Docker for easy management
- **Domain & Security:** Custom domain (to be acquired) routing through Cloudflare with strict SSL/TLS certificates for secure HTTPS access
- **Deployment Method:** Manual deployment - build locally, transfer via rsync/SCP to server, restart web server manually
- **Backup Strategy:** Git-based version control for code, manual backups of server configuration
- **Analytics:** None (no visitor tracking)

### 5. Core Features & Architecture (MVP)

| Section | Description | Key Elements |
| --- | --- | --- |
| **Hero/Header** | A welcoming introduction that establishes identity and profession | Friendly profile photo/avatar (from assets folder), clear title (e.g., Full-Stack Developer & Systems Admin), and a primary "Download CV" button |
| **Core Competencies** | A rapid-fire breakdown of technical skills to prove versatility | Grouped tags/icons for Frontend (Flutter, JS), Backend (Node.js, Python, Java), Infrastructure (Kubernetes, Docker, Linux), and AI integrations |
| **Project Showcase** | The core proof-of-work section demonstrating the "can build almost anything" capability. **3 featured projects:**<br>1. **DDOne (VoIP PBX)** - Cross-platform app (Android/iOS/Windows/MacOS), resolved critical stability issues, passed Google/Microsoft/Apple review processes<br>2. **Cammillion Trading Bot** - Python/Django, Redis, Docker, 24/7 operations on GCP, executes trades across stocks/futures/forex<br>3. **Infrastructure Enhancement** - Reduced GCP storage costs by 50% by migrating to cloud buckets, integrated Telegram reporting for scraping alerts | Emphasize the architecture, the problem solved, and independent execution |
| **Experience Timeline** | A traditional, clean chronological view of professional roles | Company names, dates, and 2-3 bullet points of measurable impact per role |
| **Contact/Footer** | A frictionless way for hiring managers to reach out | Direct email link (mailto:), LinkedIn profile link, GitHub repository link |
| **CV Download** | Hosted PDF file for easy downloading | Static PDF served from web server |

### 6. SEO Requirements
- Basic SEO implementation
- Proper meta tags (title, description, keywords)
- Proper heading structure (h1, h2, h3)
- Sitemap.xml
- robots.txt

### 7. Content Management
- Manual code updates for all content changes
- Content to be generated based on project portfolio documentation
- Existing images available in assets folder

### 8. Development Milestones

1. **Phase 1: Wireframing & Content Preparation**
   - Define the exact layout and sections
   - Generate bio text based on project portfolio
   - Prepare CV PDF
   - Organize project screenshots and assets

2. **Phase 2: Flutter Development**
   - Build the UI components for all sections
   - Implement single-page layout with smooth scrolling
   - Apply the minimalist color palette (Blue, White, Grey, Black)
   - Implement CV download functionality (hosted PDF)
   - Add direct contact links (email, LinkedIn, GitHub)

3. **Phase 3: Server Provisioning**
   - Configure the home server environment (basic machine)
   - Set up Nginx/Apache web server
   - Configure SSL/TLS certificates via Cloudflare
   - Set up domain (to be acquired)

4. **Phase 4: Testing & Launch**
   - Ensure cross-browser compatibility (Chrome, Safari, Firefox)
   - Verify mobile responsiveness of the Flutter web app
   - Test CV download functionality
   - Verify all contact links work correctly
   - Point domain to server and go live

### 9. Performance Requirements
- Basic functional performance
- No strict performance metrics (Core Web Vitals compliance not required)
- Focus on functionality over optimization

### 10. Timeline
- Flexible - no specific deadline
- Quality over speed approach
