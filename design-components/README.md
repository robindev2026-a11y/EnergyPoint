# 🎨 Design Components Library

A curated collection of animations, interactions, and UI components built during the EnergyPoint project. Each component lives in its own subfolder with full code, explanation, and a screenshot reference.

**Stack:** Vanilla HTML + CSS + JavaScript (no frameworks, no build tools)

---

## 📦 Component Index

| # | Component | Category | Complexity | Has Screenshot |
|---|-----------|----------|------------|----------------|
| 01 | [Cursor Glow](./01-cursor-glow/README.md) | Interaction / Polish | ⭐⭐ | ✅ |
| 02 | [Cinematic Loader](./02-cinematic-loader/README.md) | Animation / Entry | ⭐⭐ | ✅ |
| 03 | [Particle Canvas](./03-particle-canvas/README.md) | Background / Animation | ⭐⭐⭐ | ✅ |
| 04 | [Floating Orbs](./04-floating-orbs/README.md) | Background / Ambient | ⭐ | — |
| 05 | [Typewriter Effect](./05-typewriter-effect/README.md) | Animation / Typography | ⭐⭐ | — |
| 06 | [Glassmorphism Card](./06-glassmorphism-card/README.md) | UI Component | ⭐ | ✅ |
| 07 | [Animated Stats Counter](./07-stats-counter/README.md) | Animation / Data | ⭐⭐ | ✅ |
| 08 | [Tech Feature Marquee](./08-tech-marquee/README.md) | UI / Animation | ⭐⭐ | — |
| 09 | [Testimonials Marquee](./09-testimonials-marquee/README.md) | UI / Social Proof | ⭐⭐ | ✅ |
| 10 | [3D Card Tilt](./10-card-3d-tilt/README.md) | Interaction | ⭐⭐ | ✅ |
| 11 | [Button Ripple](./11-button-ripple/README.md) | Interaction / Micro | ⭐ | ✅ |
| 12 | [Scroll Reveal](./12-scroll-reveal/README.md) | Animation / Layout | ⭐ | — |
| 13 | [Nav Blur on Scroll](./13-nav-blur-scroll/README.md) | Navigation / Polish | ⭐ | — |
| 14 | [Hero Badge Shimmer](./14-hero-badge-shimmer/README.md) | UI / Micro-animation | ⭐ | — |
| 15 | [Benefit Card](./15-benefit-card/README.md) | UI Component | ⭐ | — |

---

## 🔧 How to Add a New Component

Run this command (or use the `document-component` skill in Antigravity):

```bash
# Create a new component folder
mkdir -p design-components/16-your-component-name

# Create the README
touch design-components/16-your-component-name/README.md

# Drop in your screenshot
# copy screenshot.png into the folder
```

Each README should follow this structure:
1. **Title + metadata** (category, complexity, dependencies)
2. **Preview** (screenshot embedded with `![](./screenshot.png)`)
3. **What It Is** — what the component does in plain English
4. **When To Use** — practical guidance
5. **HTML** — the markup
6. **CSS** — the styles
7. **JavaScript** — the interaction logic (if any)
8. **How It Works** — explanation of the key mechanics
9. **Customization** — a table of what's easy to change
10. **Used In** — link back to the file where it's used

---

## 💡 Design Principles (Learned from EnergyPoint)

- **Dark backgrounds** (#05070f) create depth — use `rgba` and `backdrop-filter` for layers
- **Cyan (#00e5ff) + Lime (#39ff14)** make a striking gradient pair for accents
- **`cubic-bezier(0.23, 1, 0.32, 1)`** is the best "springy ease-out" for hover effects
- **IntersectionObserver** > scroll listeners for performance (no continuous polling)
- **`requestAnimationFrame`** for all JS-driven animations (smooth 60fps)
- **`transition-delay`** + single IntersectionObserver = staggered grid reveals with zero complexity
- Always **hide custom cursors on mobile** (`@media (max-width: 768px) { body { cursor: auto; } }`)
- **`overflow: hidden`** + `::before` pseudo-elements = clean accent bars without extra markup

---

## 🗂️ Folder Structure

```
design-components/
├── README.md                    ← You are here
├── 01-cursor-glow/
│   ├── README.md
│   └── screenshot.png
├── 02-cinematic-loader/
│   ├── README.md
│   └── screenshot.png
├── 03-particle-canvas/
│   ├── README.md
│   └── screenshot.png
├── 04-floating-orbs/
│   └── README.md
├── 05-typewriter-effect/
│   └── README.md
├── 06-glassmorphism-card/
│   ├── README.md
│   └── screenshot.png
├── 07-stats-counter/
│   ├── README.md
│   └── screenshot.png
├── 08-tech-marquee/
│   └── README.md
├── 09-testimonials-marquee/
│   ├── README.md
│   └── screenshot.png
├── 10-card-3d-tilt/
│   ├── README.md
│   └── screenshot.png
├── 11-button-ripple/
│   ├── README.md
│   └── screenshot.png
├── 12-scroll-reveal/
│   └── README.md
├── 13-nav-blur-scroll/
│   └── README.md
├── 14-hero-badge-shimmer/
│   └── README.md
└── 15-benefit-card/
    └── README.md
```

---

*Built with EnergyPoint • Kerala's first lithium-ion experience center*
