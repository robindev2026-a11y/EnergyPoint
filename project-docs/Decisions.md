# Decisions

Important decisions and their rationale.

## 2025-06-14 - Tech Stack for Initial Delivery

**Decision:** Build the site as two self-contained static HTML files using Tailwind via CDN, GSAP via CDN, and Leaflet via CDN. No Vite, React, Next.js, or build step for phase 1.

**Context:** Client needs a fast, impressive, editable website. Heavy animations and an interactive "Experience Center" are core requirements. They want to be able to open the files locally and see results immediately.

**Rationale:** 
- Zero friction for the client to preview and hand off.
- Maximum control over animations and interactions.
- Still allows very high visual and interactive quality.
- Easy to evolve later into a proper framework if needed.

**Alternatives considered:**
- Next.js / React + Framer Motion: More powerful long-term but adds build complexity and slower local iteration for a pure marketing site.
- Pure vanilla without CDNs: Too much custom CSS/JS work for the timeline.

**Tradeoffs:** Slightly less scalable for very large future features, but dramatically faster for this scope. The current approach perfectly matches the "futuristic experience center" demo goal.

## 2025-06-14 - Lead Delivery Mechanism (WhatsApp + Email)

**Decision:** Primary automation = pre-filled WhatsApp message via `wa.me` deep link. Secondary = `mailto:` link + clipboard copy. Leads also saved to browser localStorage.

**Context:** Client wants leads sent to their WhatsApp and email automatically for promotion/follow-up.

**Rationale:**
- `wa.me` gives the best possible "one tap" experience without any backend or paid WhatsApp Business API setup.
- The message can be made very rich (includes all fields + nice formatting).
- Works immediately on mobile and desktop.
- localStorage + history view gives the client a way to see captured leads even without external systems.

**Alternatives considered:**
- EmailJS (client-side email): Good for email but still requires the user to click for WhatsApp.
- Full backend (Node + Nodemailer + WhatsApp Cloud API): Most "automatic" but introduces hosting, keys, approval process, and cost/complexity not justified for a two-page marketing site yet.

**Tradeoffs:** Requires the sales person to click the WhatsApp button (not 100% hands-off server push). However, this is extremely reliable and the formatted message makes follow-up very efficient.

## 2025-06-14 - Battery Visualization Approach

**Decision:** Implement the core "aesthetic battery" and Experience Center visuals using nested divs, CSS gradients, borders, and minimal inline SVG rather than external images, Canvas heavy drawing, or Three.js.

**Context:** Need beautiful, interactive, "see and feel" battery representations that support layer highlighting, charge animation, and environment switching.

**Rationale:**
- Keeps everything self-contained and editable in the HTML file.
- GSAP can easily animate the elements.
- Much lighter than 3D libraries.
- Easy for the client (or future developer) to tweak colors, layers, and behavior.

**Alternatives considered:**
- Three.js / React Three Fiber: Would look more "3D futuristic" but adds heavy dependencies and complexity.
- Real product photography only: Lacks the interactive "multi-layer" exploration the client specifically requested.

**Tradeoffs:** Visuals are stylized rather than photorealistic. This can be supplemented later with real photos in a gallery section.

## 2025-06-14 - Publish to GitHub

**Decision:** Initialize git, commit all current work, and publish the repository publicly on GitHub under the name "EnergyPoint" using GitHub CLI.

**Context:** The project reached a complete, self-contained, high-fidelity state (interactive landing + form with WhatsApp automation + full AI Root System docs) and needed to be version-controlled and shared.

**Rationale:**
- Provides proper source control and history.
- Makes it easy for the client to access, fork, or collaborate.
- Follows professional practice and the AI Root System post-task protocol.
- Public repo allows easy preview via GitHub Pages later if desired.

**Alternatives considered:**
- Private repo: Less discoverable and harder for client to access quickly.
- Delay publishing until more polish: Unnecessary since the core experience is already strong and functional.

**Tradeoffs:** The repo name "EnergyPoint" is simple and matches the project/brand. Placeholder contact details remain until the client provides real information.
