# FewCube - Learn the Rubik’s Cube

A single-page website for learning and exploring Rubik’s Cube methods. Built with HTML + Tailwind CSS (via CDN) and a sprinkling of modern, custom CSS for visuals like glassmorphism, aurora orbs, and a pure CSS 3D cube.

Note: The page title says “CubeCraft” while the logo/brand says “FewCube.” Pick one and update both title and brand text for consistency.

## Features

- Pure HTML + Tailwind CSS (no build step)
- Elegant glassmorphism UI with soft gradient “aurora orbs”
- CSS-only mobile navigation toggle (no JavaScript)
- Pure CSS 3D rotating cube (transform + grid)
- Beginner-friendly structure (Learn, Methods, Steps, FAQ, CTA)
- Accessible FAQ with native `<details>`/`<summary>`
- Smooth scroll and responsive layout

## Tech stack

- HTML5
- Tailwind CSS v2.2.19 (CDN)
- Custom CSS (inline in the page)
- SVG icons (inline)

Tailwind CDN included:
```html
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
```

## Getting started

- Option A (quickest): Double‑click index.html and open it in any modern browser.
- Option B (local server): Serve the file to avoid some browser restrictions.
  - Python: `python3 -m http.server 5173`
  - Node (serve): `npx serve`
  - VS Code Live Server: right‑click index.html → “Open with Live Server”

Prerequisites:
- Internet connection (Tailwind is loaded from a CDN)
- Modern browser (backdrop-filter and CSS 3D supported on current Chrome/Edge/Firefox/Safari)

## Project structure

Recommended:
```
.
├─ index.html        # The page (your file)
├─ README.md
└─ assets/           # (optional) images, downloads, favicon, etc.
```

Currently, all custom CSS is embedded in a `<style>` tag within index.html for portability.

## Sections overview

- Header: Glass nav with CSS-only mobile menu toggle
- Hero: Gradient badge, headline with text gradient, CTA buttons, and a CSS 3D cube
- Learn: Three cards covering intuition, pattern recognition, speed fundamentals
- Methods: CFOP, Roux, ZZ summaries
- Steps: Beginner layer-by-layer (7 steps + notation tip)
- FAQ: Expandable Q/A using `<details>`
- CTA: “Get the Beginner Guide” and “Compare Methods”
- Footer: Brand, anchor links, and disclaimer

## Custom CSS utilities used

- text-gradient: linear text gradient
- glass: translucent card with blur and subtle border
- hover-item, steps-item: interaction/hover effects
- faq-item: animated disclosure transitions
- orbs, grid-overlay: animated aurora background and subtle grid
- accent-line: animated gradient line
- cube-scene, cube, face, sticker: 3D cube layout and stickers
- badge, underlined: tag and section title underline styles

## Customize

- Brand and title
  - Update the `<title>` tag and the “FewCube” logo text in the header/footer.
- Colors and gradients
  - Adjust the .text-gradient and gradient backgrounds in the `<style>` section.
- Animations
  - Tweak duration/speeds in @keyframes spin, aurora, and sweep.
- Content
  - Edit the Learn, Methods, Steps, and FAQ copy to match your curriculum.
  - Link real downloads or pages to the “Get the Guide” and “Compare Methods” CTAs.
- Year auto-update (optional)
  - Add this before `</body>` to keep the footer year current:
    ```html
    <script>
      const y = document.getElementById('year');
      if (y) y.textContent = new Date().getFullYear();
    </script>
    ```

## Accessibility and UX notes

- Mobile menu toggle
  - Consider adding ARIA attributes for better screen reader support:
    - Give the menu a unique id (e.g., id="mobile-menu")
    - Add aria-controls="mobile-menu" and aria-expanded attributes to the label or convert to a `<button>` with JS if you want dynamic aria-expanded.
- Reduced motion (recommended)
  - Provide a no-motion experience for users who prefer it:
    ```css
    @media (prefers-reduced-motion: reduce) {
      .cube, .orbs::before, .orbs::after, .accent-line::after { animation: none !important; }
      html, body { scroll-behavior: auto; }
    }
    ```
- Color contrast
  - The design uses subtle opacity; validate against WCAG if you adjust colors.

## SEO tips

- Already includes a meta description. Consider adding:
  ```html
  <meta property="og:title" content="FewCube — Learn the Rubik’s Cube">
  <meta property="og:description" content="Beginner-friendly methods, speedcubing insights, and beautiful visuals.">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://yourdomain.com/">
  <meta property="og:image" content="https://yourdomain.com/og-image.jpg">
  <link rel="canonical" href="https://yourdomain.com/">
  ```
- Add a favicon and/or app icons in /assets.

## Browser support and notes

- Backdrop blur and advanced filters may not render in very old browsers.
- CSS 3D transforms are widely supported in modern browsers; performance may vary on low-power devices.

## Deployment

- GitHub Pages: push, then enable Pages in repo settings
- Netlify/Vercel: drag‑and‑drop or connect repo (framework = none/static)
- Any static host: upload index.html (+ assets)

## Upgrading Tailwind (optional)

- Tailwind v3 with the Play CDN (dev only):
  ```html
  <script src="https://cdn.tailwindcss.com"></script>
  ```
  For production, use a proper Tailwind build (PostCSS) so only used classes are shipped (tree‑shaken).

