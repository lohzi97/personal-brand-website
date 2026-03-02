# Personal Resume Website - Task List

Streamlined task breakdown focusing purely on building a **web-only** Flutter website. No mobile or desktop deployment required.

Content is extracted from `docs/CV.md` and `docs/project-portfolio.md`, assets are already in place.

## Phase 1: Project Setup

### Task 1.1: Create Flutter Project Structure

**Goal:** Set up base Flutter web-only project and create directory structure.

**Steps:**
1. Create Flutter web-only project: `flutter create --platforms web personal_resume_website`
2. Create directories: `lib/widgets/`, `lib/pages/`
3. Verify `assets/` contains: `profile.png`, `CV.pdf`, `cammillion-goals.png`, `cammillion-srifactors.png`, `ddone-google-play.jpeg`, `ddone-microsoftstore.png`

**Acceptance Criteria:**
- [ ] Flutter project created successfully
- [ ] `lib/widgets/` and `lib/pages/` directories exist
- [ ] All assets are present in `assets/`
- [ ] **Run `flutter run -d chrome` - app launches showing Flutter Demo Home Page without errors**
- [ ] No console errors or warnings

---

### Task 1.2: Configure pubspec.yaml

**Goal:** Declare assets and dependencies.

**Steps:**
1. Add to `pubspec.yaml`:
   ```yaml
   flutter:
     uses-material-design: true
     assets:
       - assets/
   ```
2. Run `flutter pub get`

**Acceptance Criteria:**
- [ ] Assets declared in pubspec.yaml
- [ ] `flutter pub get` succeeds
- [ ] **Run `flutter run -d chrome` - app launches without asset-related errors**
- [ ] Hot reload works (press `r` in terminal)

---

## Phase 2: Build Sections

### Task 2.1: Hero Section

**Goal:** Create header with profile, title, bio, and CV download.

**Content Source:** `docs/CV.md` - Sections 1-2

**Steps:**
1. Create `lib/pages/hero_section.dart`
2. Display `Image.asset('assets/profile.png')`
3. Title: "Software Engineer & Technical Problem Solver"
4. Bio: Excerpt from CV.md Section 1 ("I bridge the gap between complex code and real-world business results...")
5. CV download button linking to `assets/CV.pdf`
6. Use `url_launcher` package for CV download

**Acceptance Criteria:**
- [ ] Profile photo displays
- [ ] Title and bio from CV.md shown
- [ ] CV download button present
- [ ] **Run `flutter run -d chrome` - Hero section displays correctly**
- [ ] **Profile image loads without errors**
- [ ] **CV download button is clickable and triggers download**
- [ ] No console errors

---

### Task 2.2: Core Competencies

**Goal:** Display skills categorized from CV.md Section 5.

**Content Source:** `docs/CV.md` - Section 5

**Steps:**
1. Create `lib/pages/competencies_section.dart`
2. Display 4 categories with badge-style tags:
   - Languages: Python, Java, JavaScript, VBA, MATLAB, C, C++, C#
   - Frameworks: Django, Spring Boot, NodeJS, Flutter
   - Databases & Cloud: MySQL, Redis, SQLite, GCP, Firebase
   - DevOps & Tools: Docker, k8s, Jenkins, GlitchTip, n8n, Linux

**Acceptance Criteria:**
- [ ] All 4 categories displayed
- [ ] All skills from CV.md Section 5 included
- [ ] Tags styled consistently
- [ ] **Run `flutter run -d chrome` - Competencies section displays below Hero**
- [ ] **All badges render correctly with proper spacing**
- [ ] **Hot reload works after changes to this section**
- [ ] No console errors

---

### Task 2.3: Project Showcase

**Goal:** Display 3 featured projects with images.

**Content Source:** `docs/project-portfolio.md`

**Featured Projects:**
1. **DDOne (VoIP PBX)**
   - Image: `assets/ddone-google-play.jpeg` or `assets/ddone-microsoftstore.png`
   - Description: Section 1 of project-portfolio.md
   - Tech stack: Flutter, Janus WebRTC
   - Impact: Public release on Google/Apple/Microsoft stores
   - Link: (placeholder - add when available)

2. **Cammillion Trading Bot**
   - Image: `assets/cammillion-goals.png` or `assets/cammillion-srifactors.png`
   - Description: Section 2 (Cammillion Trading Bot)
   - Tech stack: Python, Django, GCP
   - Impact: 24/7 operations on GCP
   - Link: (placeholder - add when available)

3. **Infrastructure Enhancement**
   - Image: `assets/cammillion-srifactors.png`
   - Description: Section 3 (Financial Data Scraping)
   - Tech stack: NodeJS, Puppeteer, Docker
   - Impact: Reduced GCP storage costs by 50%
   - Link: (placeholder - add when available)

**Steps:**
1. Create `lib/pages/projects_section.dart`
2. Create card layout for each project
3. Display image, description, tech stack, impact
4. Add link button

**Acceptance Criteria:**
- [ ] All 3 projects displayed
- [ ] Project images load correctly
- [ ] Content from project-portfolio.md shown
- [ ] Tech stack displayed for each project
- [ ] **Run `flutter run -d chrome` - Projects section displays with all cards**
- [ ] **All project images load without errors**
- [ ] **Project cards have consistent layout and styling**
- [ ] **Link buttons are visible and clickable (even with placeholder URLs)**
- [ ] No console errors

---

### Task 2.4: Experience Timeline

**Goal:** Display work experience chronologically.

**Content Source:** `docs/CV.md` - Sections 2-4

**Steps:**
1. Create `lib/pages/experience_section.dart`
2. Display roles in chronological order:
   - **DotDash Technologies** (Jan 2025 - Present)
     - Company website: (placeholder)
     - Key achievements from CV.md Section 2
   - **Crea8 Capital / Celeropes** (Jan 2020 - Dec 2024)
     - Company website: (placeholder)
     - Key achievements from CV.md Section 3
   - **Freelance** (Ongoing)
     - Key achievements from CV.md Section 4

**Acceptance Criteria:**
- [ ] All 3 roles displayed in chronological order
- [ ] Achievements from CV.md shown as bullet points
- [ ] Company names link to websites (placeholders)
- [ ] **Run `flutter run -d chrome` - Experience section displays with timeline**
- [ ] **All roles show in correct chronological order**
- [ ] **Bullet points render correctly**
- [ ] **Company links are clickable (even with placeholder URLs)**
- [ ] No console errors

---

### Task 2.5: Contact Section

**Goal:** Display contact links.

**Content Source:** `docs/CV.md` - Section 1

**Steps:**
1. Create `lib/pages/contact_section.dart`
2. Display 3 links:
   - Email: `mailto:lohzian@live.com`
   - GitHub: `https://github.com/lohzi97`
   - LinkedIn: `https://www.linkedin.com/in/loh-zi-jian/`

**Acceptance Criteria:**
- [ ] Email link uses mailto:
- [ ] GitHub link points to github.com/lohzi97
- [ ] LinkedIn link points to linkedin.com/in/loh-zi-jian
- [ ] **Run `flutter run -d chrome` - Contact section displays at bottom**
- [ ] **Email link opens default email client when clicked**
- [ ] **GitHub link opens correct GitHub profile**
- [ ] **LinkedIn link opens correct LinkedIn profile**
- [ ] **All links are clearly visible and styled**
- [ ] No console errors

---

### Task 2.6: Integrate Main App

**Goal:** Connect all sections into single-page scrolling layout.

**Steps:**
1. Open `lib/main.dart`
2. Import all section widgets
3. Stack sections: Hero → Competencies → Projects → Experience → Contact
4. Implement smooth scrolling between sections
5. Apply color theme: Blue, White, Grey, Black

**Acceptance Criteria:**
- [ ] All sections render in order
- [ ] Smooth scrolling works
- [ ] Color theme consistent
- [ ] **Run `flutter run -d chrome` - Full page loads with all sections**
- [ ] **Smooth scrolling between sections works (use wheel/touch)**
- [ ] **Color theme is consistently Blue, White, Grey, Black**
- [ ] **All sections are visible without horizontal scrolling**
- [ ] No console errors

---

## Phase 3: Responsiveness

### Task 3.1: Mobile Layout

**Goal:** Ensure site works on mobile (600px breakpoint).

**Steps:**
1. Define breakpoint at 600px using `MediaQuery`
2. For each section, adapt layout:
   - Hero: Center content
   - Competencies: Stack categories vertically
   - Projects: Single column cards
   - Experience: Full width
   - Contact: Stack links vertically

**Acceptance Criteria:**
- [ ] Layout adapts at 600px breakpoint
- [ ] No horizontal scrolling on mobile
- [ ] Text is readable
- [ ] **Run `flutter run -d chrome` - Resize browser to 375px width**
- [ ] **At 375px: Hero content centers, Competencies stack vertically**
- [ ] **At 375px: Projects show single column, Experience full width**
- [ ] **At 375px: Contact links stack vertically**
- [ ] **No horizontal scrolling at any mobile width**
- [ ] No console errors

---

### Task 3.2: Desktop Layout

**Goal:** Optimize for larger screens.

**Steps:**
1. Use grid/multi-column layouts for:
   - Projects: 2-3 columns
   - Competencies: Grid of badges
2. Adjust spacing and padding for desktop

**Acceptance Criteria:**
- [ ] Desktop layout uses available width
- [ ] Grid layouts implemented
- [ ] Spacing is balanced
- [ ] **Run `flutter run -d chrome` - Resize browser to 1920px width**
- [ ] **At 1920px: Projects display in 2-3 column grid**
- [ ] **At 1920px: Competencies display in grid layout**
- [ ] **At 1920px: Spacing and padding are proportional to screen size**
- [ ] **No excessive whitespace or cramped content**
- [ ] No console errors

---

## Phase 4: SEO & Deployment Preparation

### Task 4.1: Basic SEO

**Goal:** Add meta tags to `web/index.html`.

**Steps:**
1. Edit `web/index.html`:
   - Add `<title>Loh Zi Jian - Software Engineer</title>`
   - Add meta description from CV.md Section 1
   - Add meta keywords: Flutter, Python, Java, Full-Stack Developer
2. Create `web/sitemap.xml` and `web/robots.txt` (placeholders with `yourdomain.com`)

**Acceptance Criteria:**
- [ ] Title tag added
- [ ] Meta description added
- [ ] sitemap.xml and robots.txt created
- [ ] **Run `flutter run -d chrome` - Browser title shows correctly**
- [ ] **Inspect page source - verify meta tags are present**
- [ ] **sitemap.xml and robots.txt are accessible via browser dev tools**
- [ ] No console errors

---

### Task 4.2: Production Build & Test

**Goal:** Create production build and test locally.

**Steps:**
1. Build: `flutter build web --release`
2. Serve `build/web/` with `python -m http.server 8000`
3. Test at `http://localhost:8000`
4. Verify all sections load
5. Test all links (CV, GitHub, email)
6. Test responsive behavior using browser dev tools

**Acceptance Criteria:**
- [ ] Production build succeeds
- [ ] Site serves correctly
- [ ] All sections load
- [ ] All links work
- [ ] Responsive behavior verified
- [ ] **Build completes without errors**
- [ ] **Navigate to http://localhost:8000 - all sections render correctly**
- [ ] **CV download works in production build**
- [ ] **GitHub link works in production build**
- [ ] **Email link works in production build**
- [ ] **LinkedIn link works in production build**
- [ ] **Test at 375px width - responsive layout works**
- [ ] **Test at 1920px width - desktop layout works**
- [ ] **No console errors in production build**

---

## Phase 5: Infrastructure (Placeholders)

### Task 5.1: Docker Setup (For Later)

**Steps:**
1. Create `Dockerfile` for Nginx
2. Create `nginx.conf` with SPA routing
3. Create `docker-compose.yml`
4. (Configure on your home server when ready)

---

### Task 5.2: Deployment (For Later)

**Steps:**
1. Build Flutter web: `flutter build web --release`
2. Transfer to server: `rsync -avz build/web/ user@server:/path/to/nginx/html/`
3. Restart Docker: `docker-compose up -d --build`
4. Configure Cloudflare DNS and SSL (when domain is ready)
