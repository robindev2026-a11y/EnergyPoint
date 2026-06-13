# AI Context

## Current Project State

The EnergyPoint website is a two-page static marketing site for a lithium-ion battery Experience Center in Kerala.

- **index.html**: Fully functional futuristic landing page with:
  - Animated hero battery (click to charge)
  - Interactive Traditional vs Lithium comparison with animated metric bars
  - Three use-case cards (Residential, Commercial, Industrial)
  - Multi-layer Experience Center (4 clickable layers + 3 environment modes + draggable charge interaction)
  - Benefits grid
  - Interactive Leaflet map at the bottom
  - Heavy use of GSAP, CSS animations, glassmorphism, neon accents

- **form.html**: Lead capture form with premium design that:
  - Collects name, phone, email, location, interest type, capacity, message
  - On submit shows success panel
  - Primary action: "Open WhatsApp with full details" (wa.me prefilled)
  - Secondary: mailto email + copy to clipboard
  - Leads are also persisted in localStorage for demo/review

Current implementation is self-contained (no build step). Can be opened directly in a browser.

## Active Priorities

1. Replace all placeholder contact information (WhatsApp number, address, phone, email) with real business details.
2. Finalize and polish the visual/interactive "Experience Center" section so it feels like a real multi-sensory showroom.
3. Ensure lead capture reliably delivers complete, well-formatted information via WhatsApp (primary) and email (secondary).
4. Add any missing high-impact visuals or micro-interactions requested by the client.
5. Prepare the site for easy handoff / static hosting.

## Important Context

- The client is a supplier of lithium-ion batteries (LFP chemistry preferred for safety and longevity) targeting residential, commercial, and industrial customers in Kerala.
- Core messaging: Zero maintenance, 5-year warranty, dramatically longer life, higher efficiency, no replacements compared to traditional lead-acid batteries.
- The "Experience Center" concept is central — visitors should be able to "see and feel" the batteries through rich interactive web experiences.
- Futuristic, premium, animated aesthetic is non-negotiable.
- Kerala-specific considerations (humidity, heat, tropical conditions) are relevant for LFP advantages.

## Current Constraints

- Must remain easy to edit and view locally (currently using Tailwind CDN + external CDNs for GSAP/Leaflet). Avoid complex build tools unless the client specifically requests a full framework migration.
- Real automated WhatsApp sending (without user clicking) requires WhatsApp Business API / Meta approval — currently out of scope. We use the best possible client-side automation (prefilled wa.me).
- No real backend yet for lead persistence or automated emails. Current solution uses localStorage + mailto + wa.me.
- Map is using free OpenStreetMap/Leaflet — no API keys required but may need address refinement.
- Images: Currently using pure CSS/SVG for the battery visuals. Real product photography can be added later.

## Frequently Touched Areas

- `index.html` — main landing + all interactive components (hero battery, comparison logic, Experience Center layers/environments, map)
- `form.html` — lead form, submission handler, WhatsApp/email automation
- `project-docs/` — all AI Root System documentation (this folder)

## AI Operating Notes

- When the user says "update the site", prefer making targeted enhancements to existing sections rather than large refactors.
- Always keep the interactive, animated, "experience center" personality strong.
- Before changing the form submission flow, re-read the WhatsApp prefill logic and ensure the lead message remains rich and useful for the sales team.
- For any new feature, consider whether it strengthens the "see it, feel it" multi-layer exploration theme.
- Document every meaningful decision in Decisions.md immediately.
