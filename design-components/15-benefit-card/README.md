# 15 — Benefit Card with Accent Bar

**Category:** UI Component / Layout  
**Complexity:** ⭐ Easy  
**Dependencies:** None — Pure CSS

---

## What It Is

A variation of the glassmorphism card specifically designed for **benefit/feature grids**. Features:
- Large stat number with gradient text at the top
- A gradient **accent bar** that appears at the top edge on hover
- Subtle lift animation on hover
- Works in a 2 or 3-column grid

---

## When To Use

- "Benefits" or "Features" sections
- Pricing comparison tables
- Stats + context grids
- Any place where you show a number + explanation

---

## HTML

```html
<div class="benefit-grid">
  <div class="benefit-card">
    <div class="benefit-stat">0</div>
    <div class="benefit-title">Maintenance Required</div>
    <div class="benefit-desc">No watering. No cleaning. No equalizing. Install and forget.</div>
  </div>

  <div class="benefit-card">
    <div class="benefit-stat">6000+</div>
    <div class="benefit-title">Deep Discharge Cycles</div>
    <div class="benefit-desc">15+ years of daily use. Traditional batteries die in 2–4 years.</div>
  </div>

  <div class="benefit-card">
    <div class="benefit-stat">97%</div>
    <div class="benefit-title">Round-Trip Efficiency</div>
    <div class="benefit-desc">You get almost every watt you put in.</div>
  </div>
</div>
```

---

## CSS

```css
.benefit-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1rem;
}

.benefit-card {
  /* Glassmorphism base */
  background: rgba(10, 15, 30, 0.75);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(0, 229, 255, 0.12);
  border-radius: 1.5rem;
  padding: 1.75rem;

  position: relative;
  overflow: hidden;    /* Clips the accent bar */

  /* Smooth transitions */
  transition:
    transform   0.3s cubic-bezier(0.23, 1, 0.32, 1),
    border-color 0.3s ease,
    box-shadow  0.3s ease;
}

/* Gradient accent bar (hidden → visible on hover) */
.benefit-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(to right, #00e5ff, #39ff14);
  opacity: 0;
  transition: opacity 0.3s ease;
}
.benefit-card:hover::before { opacity: 1; }

/* Hover state */
.benefit-card:hover {
  transform: translateY(-4px);
  border-color: rgba(0, 229, 255, 0.2);
  box-shadow: 0 16px 32px rgba(0, 0, 0, 0.25);
}

/* Gradient stat number */
.benefit-stat {
  font-size: 2.5rem;
  font-weight: 700;
  letter-spacing: -0.04em;
  margin-bottom: 1.5rem;
  font-variant-numeric: tabular-nums;

  background: linear-gradient(135deg, #00e5ff 0%, #39ff14 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.benefit-title {
  font-size: 1.25rem;
  font-weight: 600;
  letter-spacing: -0.02em;
  margin-bottom: 0.5rem;
}

.benefit-desc {
  font-size: 0.875rem;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.6);
}
```

---

## How It Works

1. Same base as the glassmorphism card
2. `::before` pseudo-element provides the top accent bar — absolutely positioned at `top: 0`
3. The `2px` height makes it a thin line, the gradient gives it the cyan-to-lime look
4. `overflow: hidden` clips it so it sits flush at the very top edge
5. `opacity: 0 → 1` transition on hover fades it in
6. The stat number uses the gradient text technique (background-clip + text-fill-color transparent)

---

## Customization

| Property | Where |
|---|---|
| Accent bar colors | `linear-gradient(to right, #00e5ff, #39ff14)` in `::before` |
| Accent bar thickness | Change `height: 2px` |
| Stat number size | `font-size: 2.5rem` in `.benefit-stat` |
| Stat gradient | `background: linear-gradient(...)` in `.benefit-stat` |
| Lift amount | `translateY(-4px)` |
| Grid columns | `minmax(280px, 1fr)` — change 280px for wider/narrower cards |

---

## Combination Tip

For **maximum visual impact**, use `.benefit-card` inside a grid with `.reveal` and stagger delays:
```html
<div class="benefit-card reveal reveal-delay-1">...</div>
<div class="benefit-card reveal reveal-delay-2">...</div>
<div class="benefit-card reveal reveal-delay-3">...</div>
```

---

## Used In
- [EnergyPoint/index.html](../index.html) — Benefits section (6-card grid)
