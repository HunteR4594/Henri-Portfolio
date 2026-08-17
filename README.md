# Henri-Portfolio

### Hello there! I am John Henri, and this is my portfolio.
###### Portfolio Link: https://hunter4594.github.io/Henri-Portfolio/#Home
- It contains a little bit of me, my works, and skills. You can also see here my contacts.

## Table of Contents
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Sections](#sections)
- [How to run this file locally?](#how-to-run-this-file-locally)
- [Adding a New Project to the Projects Table](#adding-a-new-project-to-the-projects-table)
- [Configuring the Contact Form (EmailJS)](#configuring-the-contact-form-emailjs)
- [Deployment](#deployment)

## Overview
A single-page personal portfolio site built with plain HTML, CSS, and JavaScript — no build step, no framework, no bundler. It's deployed as a static site directly to GitHub Pages from this repository.

## Tech Stack
- **HTML/CSS/JS** — no build tooling; `index.html` is the entire page.
- **[Bootstrap 5.3.3](https://getbootstrap.com/)** (CDN) — grid, navbar, modal, carousel, and form components.
- **[tsParticles](https://particles.js.org/) `tsparticles-slim`** (CDN) — the floating particle backgrounds on the Home and Contact sections.
- **[EmailJS](https://www.emailjs.com/) `@emailjs/browser`** (CDN) — sends the Contact form directly from the browser, no backend required.
- **Google Fonts** — Archivo Black for display headings.

All third-party libraries are loaded from CDN in `index.html`; there is nothing to `npm install` to run the site.

## Project Structure
```
Henri-Portfolio/
├── index.html            # The entire site: markup for every section + the project modal template
├── portfolio.css         # All custom styling (glass-effect cards, animations, responsive tweaks)
├── script.js             # All behavior (see below)
├── assets/
│   ├── logo.svg           # Favicon / navbar logo
│   ├── me.jpg              # Profile photo
│   ├── Mypicture (1).svg   # Hero illustration
│   ├── John_Henri_Reas_Resume.pdf
│   ├── *.mp4 / *.webm      # Background videos for About / Skills / Projects sections
│   ├── 2.png, 3.png        # Decorative parallax spheres
│   └── gallery/            # Per-project screenshot folders, one per Projects-table row
│       ├── GmailCategorizationAutomation/
│       ├── OutreachLeadTracker/
│       ├── LostandFound/
│       ├── POS/
│       ├── TimePaws/
│       ├── diarago/
│       ├── COBOLCaseStudy/
│       ├── DSACaseStudy/
│       └── CCaseStudy/
└── README.md
```

`script.js` is organized into four numbered blocks (see the comments in the file):
1. **EmailJS initialization** — sets the public key used by the Contact form.
2. **Intersection Observer & typing effect** — fades in `.block`/`.lblock`/`.rblock` elements as they scroll into view, and types out the name/role in the hero once `#NameRole` is visible.
3. **Project gallery modal** — populates the shared `#projectGalleryModal` (title, image carousel, description, features, tech stack, role) from whichever project row was clicked, using that row's `data-*` attributes.
4. **Particles, contact form, and misc animations** — tsParticles setup for the hero/contact backgrounds, the EmailJS submit handler, the profile picture's holographic tilt effect, the navbar scroll effect, and the parallax scroll effects on the decorative spheres/particles.

## Sections
The page is a single scrollable document with four anchored sections, linked from the navbar:

| Section | Anchor | Contents |
|---|---|---|
| Home | `#Home` | Hero intro, name/role typing effect, profile card, quick stats (years experience, project count), resume download, social links |
| About | `#About` | My Story, My Purpose, and Credentials (Academic, Leadership & Organization, Certification, Achievement) |
| Skills | `#Skills` | Four cards — Programming Languages, Frameworks and Tools, Soft Skills (progress bars), and Testing & Data Analysis |
| Projects | `#Projects` | A table of projects; clicking a row opens a shared modal with a screenshot carousel, description, key features, tech stack, and role |
| Contact | `#Contact` | A form wired to EmailJS, plus decorative particle background |

## How to run this file locally?
1. Find the repository URL and copy the URL displayed under the HTTPS tab.

   <img width="981" height="643" alt="image" src="https://github.com/user-attachments/assets/8d9a91af-e38d-4dfc-b9e0-06897b4e90b4" />

2. Open your terminal and navigate a file where you want to store the project.

  <img width="1180" height="612" alt="image" src="https://github.com/user-attachments/assets/41b48c3a-d733-4349-abc1-3533ba810488" />

  <img width="1178" height="602" alt="image" src="https://github.com/user-attachments/assets/18fc4a10-a5a2-4d87-ac90-7c33c741896f" />

3. Clone the repository using the git clone command.

   <img width="1180" height="601" alt="image" src="https://github.com/user-attachments/assets/55926f74-f6de-4454-9f54-06543a65a729" />

   <img width="1179" height="608" alt="image" src="https://github.com/user-attachments/assets/b8ef9c41-fd13-4b40-bf90-73ba8cd7a022" />

4. Now you can navigate to the prject folder of the cloned repository.

  <img width="1177" height="600" alt="image" src="https://github.com/user-attachments/assets/82ae6ce5-84b9-45e3-9e54-c59502e0262f" />

5. Look for the README.md as it almost always contains the documentation on how to run the project. Because some projects has installation guide that needs to be done first before you run the project.
   - For this project, we can run it by opening the index file as it only contains html, css, and javascript. Since there is no build step, either double-click `index.html` to open it in your browser, or serve it locally for a closer match to production:
     ```
     python -m http.server 8000
     ```
     then visit `http://localhost:8000`.

## Adding a New Project to the Projects Table
The Projects table (`index.html`, inside `<section id="Projects">`) is hand-written HTML — each project is one `<tr>`, not generated from a data file. Every row carries `data-*` attributes that the shared modal (`#projectGalleryModal`, populated by the script in `script.js`, block 3) reads when that row is clicked:

| Attribute | Purpose | Delimiter |
|---|---|---|
| `data-project-title` | Modal heading | — |
| `data-images` | Screenshot carousel image paths | comma (`,`) |
| `data-description` | Full project description (modal only) | — |
| `data-features` | Key Features list | question mark (`?`) |
| `data-stack` | Tech Stack badges | question mark (`?`) |
| `data-role` | Your role on the project | — |

To add a project:
1. Create a folder under `assets/gallery/<project-name>/` with its screenshots.
2. Copy an existing `<tr>` block and update its `data-*` attributes and visible `<td>` cells (Date, Name, short Tech Stack badges, short Description).
3. No changes are needed to the modal template itself — it's reusable and picks up new rows automatically.

Note the delimiter convention: within `data-features` and `data-stack`, use `?` to separate items (not `,`), since individual items may themselves contain commas (e.g. `Supabase (Auth, PostgREST, RLS)`).

## Configuring the Contact Form (EmailJS)
The Contact form submits via [EmailJS](https://www.emailjs.com/) directly from the browser — there's no backend. Configuration lives in `script.js`:
- **Public key** — block 1, `emailjs.init({ publicKey: "..." })`
- **Service ID / Template ID** — block 4, inside the `contact-form` submit handler (`serviceID`, `templateID`)

These correspond to an EmailJS account, email service, and template configured on [emailjs.com](https://www.emailjs.com/).

## Deployment
The site is deployed via **GitHub Pages** directly from this repository (no build/publish step — GitHub Pages serves `index.html` as-is) at:
https://hunter4594.github.io/Henri-Portfolio/
