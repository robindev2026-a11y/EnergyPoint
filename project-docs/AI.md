# Project AI Entry Point

This project inherits the AI Root System.

## Purpose

EnergyPoint is Kerala's premier lithium-ion (LFP) battery Experience Center. The project delivers a high-impact, futuristic two-page marketing website designed to educate visitors on the superiority of lithium-ion batteries over traditional lead-acid, showcase an interactive "multi-layer experience center," and capture qualified leads for the business.

The website must feel premium, animated, and immersive — reflecting the cutting-edge nature of the product.

## Mandatory Pre-Task Protocol

Before starting significant work, read:

1. `AI.md`
2. `AIContext.md`
3. `Architecture.md`
4. `DevelopmentStandards.md`
5. `KnownIssues.md`
6. `PlannedFeatures.md`
7. `DeferredWork.md`
8. `Decisions.md`

For small tasks, read the smallest safe subset, but never act without enough project context.

## Project Boundaries

**What this project owns:**
- The complete two-page website (index.html + form.html)
- All visual design, animations, interactivity, and user experience
- Lead capture flow including WhatsApp prefill automation and email path
- Static assets and self-contained implementation (Tailwind CDN + GSAP + Leaflet)
- Documentation inside `project-docs/`

**What this project does not own:**
- Backend server / database for lead storage (currently browser localStorage + client-side actions)
- Real WhatsApp Business API integration (currently uses wa.me deep links)
- Actual product manufacturing, inventory, or physical Experience Center operations
- Hosting, domain, or production deployment infrastructure (to be decided)
- Physical marketing materials, photography of real batteries, or legal/compliance content

**External systems / dependencies:**
- WhatsApp (wa.me links for lead delivery)
- Email (currently mailto fallback; future EmailJS or backend)
- Leaflet.js + OpenStreetMap tiles for the map
- GSAP + ScrollTrigger (CDN)
- Tailwind CSS (CDN for current version)

## Post-Task Protocol

After significant work:
1. Update relevant project documents (especially AIContext.md, Architecture.md, Decisions.md).
2. Record important decisions in `Decisions.md`.
3. Add future work to `PlannedFeatures.md` or `DeferredWork.md`.
4. Add bugs or risks to `KnownIssues.md`.
5. Consider whether any learning should be promoted to Obsidian (via the global knowledge system).
6. Consider whether the AI Root System should evolve.

## Global Tools

- Use the root framework for knowledge rules.
- Use the context system if this project has machine-readable memory enabled.
- Use the commit assistant if committing changes.

## Current Project Status (summary)

See AIContext.md for detailed state, priorities, and constraints. The site is currently a high-fidelity, fully interactive prototype built as self-contained static HTML files.

## How to Work in This Project

- Always prefer enhancing the existing interactive sections (comparison, Experience Center layers, battery visuals) over adding new pages unless explicitly requested.
- Keep the "futuristic experience center" feeling as the north star for any new animations or UI.
- When touching form logic, always maintain the one-click WhatsApp prefill experience as the primary automation.
- Update docs immediately after changes that affect architecture, user flow, or key decisions.
