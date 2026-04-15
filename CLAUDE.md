# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

phd-persson.se is a static website that presents the work of Ph.D. Per Persson, including publications and blog-posts. 
The site is built with vanilla HTML, CSS, and JavaScript - no build tools or frameworks.

## Development

**Local preview:** Open any HTML file directly in a browser, or use a local server:
```bash
python3 -m http.server 8000
# or
npx serve .
```

**Deployment:** Static files hosted on GitHub Pages. Pretty URLs work via directory structure with index.html files.

## Architecture

### URL Structure (Pretty URLs)
```
/                    → index.html
/publikationer       → publikationer/index.html
/blogg               → blogg/index.html
/blogg/20-80         → blogg/20-80/index.html
/tjanster/           → tjanster/index.html
```

All internal links use **relative paths** (e.g., `../publikationer/`, `./blogg/rubrik/`) to support GitHub Pages deployment under a repository subpath. 
New blog-posts pages go under `blogg/[name]/`.

### CSS Architecture
- **Mobile First** with breakpoints at 640px and 1024px
- CSS custom properties (design tokens) in `:root` for colors, spacing, typography
- WCAG 2.1 AA compliant color combinations
- Minimum 44px touch targets for interactive elements

### JavaScript Modules (js/main.js)
- Mobile navigation toggle with focus trapping
- Modal dialogs with ARIA attributes and keyboard navigation
- Tab component for documentation page (arrow keys, Home/End support)
- Screen reader announcements via live region
- Respects `prefers-reduced-motion`

## Open Graph

All pages must include Open Graph metadata for social media sharing. Add these meta tags in the `<head>` section:

```html
<!-- Open Graph -->
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Page description">
<meta property="og:image" content="https://kommuna.se/images/[image-name]-og.png">
<meta property="og:type" content="website">
```

**Important:**
- `og:image` must use **absolute URLs** (e.g., `https://phd-persson/images/...`)
- Images should be 1200x630 pixels (PNG format)
- General pages use `phd-persson-og.png`, service pages use service-specific images (e.g., `blog-og.png`)

**Image files location:** `images/` directory contains both SVG source icons and PNG files for Open Graph.

## Language

All content is in Swedish. UI labels, ARIA attributes, and screen reader announcements use Swedish text.
