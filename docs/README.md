# Project Breakdown: DDG Website

This documentation provides a comprehensive overview of the `ddg-website` codebase, its architecture, key components, and maintenance recommendations.

---

## 1. Project Overview
The `ddg-website` is a static marketing website for a door and gate service company. It is designed to provide information about residential and commercial services, with optimized experiences for both desktop and mobile users.

## 2. Core Architecture & Routing
The site uses a simple client-side redirection pattern at the root to handle mobile vs. desktop experiences.

- **`index.html`**: The entry point. It contains JavaScript that detects the user's device (`navigator.userAgent`) and redirects them:
  - **Mobile users** are sent to `mobile.html`.
  - **Desktop users** are sent to `desktop.html`.

## 3. Directory Structure & Key Files

### Root Directory
- `index.html`: Main entry point / router.
- `desktop.html`: Primary residential landing page for desktop users.
- `mobile.html`: Optimized residential experience for mobile users.
- `commercial.html`: Dedicated page for commercial door and dock services.
- `embed_vars.sh`: (Legacy) A shell script containing base64 encoded images.

### Directories
- **`css/`**: External stylesheets for each major page (`desktop.css`, `mobile.css`, `commercial.css`).
- **`images/`**: Optimized JPG and PNG assets. Includes extracted images from `commercial.html` (prefixed with `comm_`).
- **`archive/`**: Contains backup files, conceptual layouts, and unused assets to keep the root clean.
- **`docs/`**: Project documentation.

### Infrastructure
- **`.github/workflows/deploy.yml`**: Automates deployment to GitHub Pages upon pushing to the main branch.

## 4. Major Components & Technologies
- **Technologies**: Pure HTML5 and CSS3.
- **Styling**: Styles are externalized in the `css/` directory for better maintainability and caching.
- **Asset Management**: Images are stored as external files in `images/`, avoiding HTML bloat from Base64 encoding.

## 5. Deployment Workflow
The project is configured for **GitHub Pages**.
1. Code is pushed to the repository.
2. The GitHub Action in `.github/workflows/deploy.yml` triggers.
3. The static files are bundled and deployed to the GitHub Pages environment.

## 6. Maintenance & Optimization Performed

### Performance Optimization
- **Base64 Extraction**: Extracted heavy embedded images from `commercial.html` into the `images/` folder, reducing the HTML file size from ~660KB to ~8KB.

### Code Organization
- **CSS Externalization**: Moved large internal `<style>` blocks to a dedicated `css/` directory.
- **Archive System**: Moved duplicate files (`residential.html`), staging pages (`concepts.html`), and various `.backup.html` files to an `archive/` folder.

### SEO & Fixes
- **Meta Tags**: Added missing SEO descriptions and standardized titles.
- **Link Fixes**: Converted hardcoded external raw GitHub links to relative local paths.
- **Placeholder Cleanup**: Replaced development placeholders and incorrect contact info in `desktop.html` with accurate local data.
