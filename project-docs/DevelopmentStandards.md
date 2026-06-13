# Development Standards

Project-specific engineering standards for the EnergyPoint website.

## Coding Style

- Use semantic, readable HTML with clear section comments.
- Keep JavaScript in `<script>` tags at the bottom of each HTML file (no separate .js files for the current phase).
- Prefer vanilla JS + GSAP over heavy frameworks.
- Use Tailwind utility classes heavily; extract repeated patterns into custom CSS only when necessary.
- All animations should feel smooth and "premium" — use `cubic-bezier(0.23, 1, 0.32, 1)` for most transitions.
- Maintain the dark futuristic aesthetic (#05070f background, glass effects, cyan #00e5ff + lime #39ff14 accents).

## Naming

- HTML ids and classes: Use kebab-case or descriptive camelCase for JS targets (e.g. `xp-battery`, `comparison-metrics`).
- JavaScript functions: `camelCase` (e.g. `activateLayer`, `setEnvironment`, `handleSubmit`).
- CSS custom properties and key classes should clearly communicate purpose (e.g. `.futuristic-card`, `.neon-cyan`).

## Folder Structure

Current (lightweight):
- `/` — `index.html`, `form.html`, `README.md`
- `/project-docs/` — All AI Root System knowledge files
- `/assets/` — Reserved for future images, css, js (currently mostly empty)

When adding real assets later, organize under `assets/images/`, `assets/css/`, etc.

## Testing

- Manual browser testing is primary (Chrome, Safari, Firefox).
- Test on mobile (responsive behavior of Experience Center, form, comparison).
- Always verify that interactive elements (layer clicks, environment switches, hero battery, form submission) continue to work after changes.
- No automated test suite at this stage.

## Commits

- Use clear, descriptive commit messages.
- Group related changes (e.g. "feat: enhance Experience Center layer highlighting + info panel").
- Consider using the AI commit assistant when available.

## AI Workflow Rules

- Always read the mandatory project-docs files (see AI.md) before significant changes.
- Prefer enhancing existing interactive sections over creating new pages.
- When modifying form logic, protect the quality and completeness of the WhatsApp prefilled message.
- After any non-trivial change, update the relevant project-docs files (especially AIContext.md, Decisions.md, and Architecture.md if structural).
- Keep the "multi-layer experience center" feeling as the primary creative constraint for new features.
