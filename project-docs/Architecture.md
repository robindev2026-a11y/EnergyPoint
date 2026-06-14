# Architecture

## Overview

EnergyPoint is a lightweight, self-contained static website consisting of two HTML pages. The architecture prioritizes instant local preview, maximum animation/interactivity fidelity, and zero deployment friction for the initial phase.

The site uses a "futuristic experience center" metaphor delivered entirely through client-side HTML, CSS (Tailwind via CDN), and JavaScript (vanilla + GSAP + Leaflet).

## Components

- **index.html (Landing Page)**
  - Hero with interactive battery visual
  - Live comparison engine (Traditional vs Lithium)
  - Use case cards (Residential / Commercial / Industrial)
  - Multi-layer Experience Center visualizer (the core interactive experience)
  - Benefits grid
  - Location + interactive map section

- **form.html (Lead Capture Page)**
  - Premium form with interest pills
  - Submission handler
  - Success state with WhatsApp primary action
  - Mailto + clipboard secondary actions
  - Local lead storage for review

- **Styling & Interactivity Layer**
  - Tailwind CSS (CDN)
  - GSAP + ScrollTrigger (CDN)
  - Custom CSS for neon/glass/futuristic effects
  - Vanilla JS for all interactions (comparison bars, layer highlighting, environment switching, battery charge dragging, form handling, map)

- **Map**
  - Leaflet.js + OpenStreetMap (CDN, no API key)

- **Deployment**
  - GitHub repository: `https://github.com/robindev2026-a11y/EnergyPoint`
  - Public site: `https://robindev2026-a11y.github.io/EnergyPoint/`
  - GitHub Actions workflow: `.github/workflows/deploy-pages.yml`
  - Deployment trigger: pushes to `main` and manual `workflow_dispatch`

## Data Flow

- All data is client-side only.
- Form submission does **not** send data to a server. Instead:
  1. Data is collected in JS.
  2. Formatted into a rich text block.
  3. Used to construct a `wa.me` URL (primary).
  4. Optionally used for `mailto:` or clipboard.
  5. Also persisted to `localStorage` under `energypoint_leads`.

- No backend, database, or API calls (except map tile loading).
- Deployment uploads the static project root as the GitHub Pages artifact.

## Module Boundaries

- The two HTML files are intentionally separate pages (no shared JS bundle).
- Most complex logic lives inside `<script>` tags in each file.
- Visual battery components are implemented with nested divs + CSS gradients + minimal SVG rather than external image assets (for now).

## External Dependencies

- Tailwind CSS (playground CDN)
- GSAP 3.12.5 + ScrollTrigger (cdnjs)
- Leaflet 1.9.4 (unpkg)
- OpenStreetMap tiles
- GitHub Pages / GitHub Actions for static hosting

## Architectural Decisions

See `Decisions.md` for detailed records. Major choices include:
- Static HTML + CDN libraries (speed of iteration + zero build step)
- wa.me deep link as primary "automation" mechanism for WhatsApp
- Pure CSS/SVG battery visuals instead of 3D libraries (to keep it lightweight and editable)

## Constraints

- Must work when opened directly from the file system (file:// protocol).
- Must feel highly animated and premium without heavy frameworks.
- Lead delivery must be useful even without a backend.
