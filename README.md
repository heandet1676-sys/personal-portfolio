# Hean Det — Personal Portfolio Website

A modern, premium, and fully responsive personal portfolio website built with **Vue.js 3**, **Bootstrap 5**, and **Vite**.

## Tech Stack

- **Framework**: Vue.js 3 (Composition-ready Options API)
- **Styling**: Bootstrap 5 + Custom CSS with CSS Variables
- **Build Tool**: Vite 8
- **Fonts**: Inter + JetBrains Mono (Google Fonts)
- **Icons**: Inline SVG (no dependencies)

## Project Structure

```
hean-portfolio/
├── src/
│   ├── components/
│   │   ├── NavBar.vue           # Sticky responsive navigation
│   │   ├── HeroSection.vue      # Hero with particle canvas & animations
│   │   ├── AboutSection.vue     # About + stats + profile image
│   │   ├── SkillsSection.vue    # Categorized skills with progress bars
│   │   ├── ProjectsSection.vue  # Project cards with filter tabs
│   │   ├── ExperienceSection.vue # Vertical timeline
│   │   ├── EducationSection.vue # Education + certifications
│   │   ├── ServicesSection.vue  # Services grid
│   │   ├── GitHubSection.vue    # GitHub stats + contribution grid
│   │   ├── ContactSection.vue   # Contact form + social links
│   │   └── FooterSection.vue    # Footer with nav & social
│   ├── App.vue                  # Root app with scroll reveal
│   ├── main.js                  # Entry point
│   └── style.css                # Global CSS variables & utilities
├── index.html                   # SEO-optimized HTML
└── vite.config.js
```

## Getting Started

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Customization

### Personal Information
Update the following files with your real information:

- **`src/components/ContactSection.vue`** — email, phone, location, social URLs
- **`src/components/FooterSection.vue`** — social URLs
- **`src/components/HeroSection.vue`** — name, title, description
- **`src/components/AboutSection.vue`** — bio text, stats numbers

### Profile Photo
Replace the placeholder in `HeroSection.vue` and `AboutSection.vue`:
- Add your photo to `src/assets/`
- Replace the SVG placeholder with `<img src="@/assets/your-photo.jpg" alt="Hean Det" />`

### Projects
Edit the `projects` array in `src/components/ProjectsSection.vue` with real project links.

### Social Links
Search for `heandet` across all component files and replace with your actual handles.

## Deployment

This project is ready to deploy to:
- **Netlify**: `npm run build` → deploy `dist/` folder
- **Vercel**: Connect repo, auto-detected as Vite project
- **GitHub Pages**: Use `vite-plugin-gh-pages`

## Design System

The design uses CSS custom properties defined in `src/style.css`:

| Variable | Value |
|---|---|
| `--bg-primary` | `#0a0a0f` |
| `--accent` | `#6366f1` (Indigo) |
| `--cyan` | `#06b6d4` |
| `--purple` | `#a855f7` |
| `--font-mono` | JetBrains Mono |

---

© 2026 Hean Det. All rights reserved.
