# 14 — Hero Badge Shimmer

**Category:** UI Component / Micro-animation  
**Complexity:** ⭐ Easy  
**Dependencies:** None — Pure CSS

---

## What It Is

A small pill-shaped badge (often used as a "LIVE" indicator or eyebrow label above headings) with a **light sweep shimmer animation** that passes across it periodically. The shimmer is a `::after` pseudo-element with a gradient that translates off-screen and repeats.

---

## When To Use

- "NEW", "LIVE", "BETA", "KERALA'S FIRST" type labels
- Any status indicator badge
- Eyebrow labels above hero headings
- Feature announcement badges

---

## HTML

```html
<div class="hero-badge">
  <div class="badge-dot"></div>
  KERALA'S FIRST EXPERIENCE CENTER
</div>
```

---

## CSS

```css
.hero-badge {
  position: relative;
  overflow: hidden;                      /* clips the sweeping shimmer */
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0 1rem;
  height: 2rem;
  border-radius: 99px;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.1);
  font-size: 0.7rem;
  letter-spacing: 0.15em;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.8);
}

/* The shimmer sweep */
.hero-badge::after {
  content: '';
  position: absolute;
  top: -50%;
  left: -60%;               /* starts off-screen left */
  width: 35%;
  height: 200%;
  background: linear-gradient(
    120deg,
    transparent 20%,
    rgba(255, 255, 255, 0.25) 50%,  /* white highlight */
    transparent 80%
  );
  transform: skewX(-20deg);         /* angled light beam */
  animation: badge-shimmer 3.5s ease-in-out infinite;
}

@keyframes badge-shimmer {
  0%   { left: -60%; }    /* starts off-screen left */
  40%  { left: 130%; }    /* sweeps through and exits right */
  100% { left: 130%; }    /* stays off-screen until next cycle */
}

/* Pulsing status dot */
.badge-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: #39ff14;     /* lime green = "active/live" */
  animation: pulse-dot 2s ease-in-out infinite;
}

@keyframes pulse-dot {
  0%, 100% { opacity: 1; transform: scale(1); }
  50%       { opacity: 0.6; transform: scale(0.85); }
}
```

---

## How It Works

1. `::after` creates a diagonal light beam element using `skewX(-20deg)`
2. The beam is a gradient: `transparent → white → transparent` (mimics a light reflection)
3. The `badge-shimmer` keyframe moves it from `-60%` (off-screen left) to `130%` (off-screen right)
4. It moves 0% → 40% of the animation time, then **holds** at 130% for the remaining 60%
5. This creates a "flash every 3.5 seconds" pattern (not a constant slide)
6. `overflow: hidden` on the badge clips the beam so it doesn't leak outside

---

## Customization

| Property | Where |
|---|---|
| Shimmer frequency | Change `3.5s` — shorter = more frequent |
| Shimmer brightness | Change `rgba(255,255,255,0.25)` — higher alpha = brighter |
| Beam angle | Change `skewX(-20deg)` and `120deg` in gradient |
| Beam width | Change `width: 35%` |
| Dot color | `background: #39ff14` |
| Background | `background: rgba(255,255,255,0.04)` |

---

## Variants

**Cyan shimmer instead of white:**
```css
background: linear-gradient(
  120deg,
  transparent 20%,
  rgba(0, 229, 255, 0.3) 50%,
  transparent 80%
);
```

**Continuous shimmer (no pause):**
```css
@keyframes badge-shimmer {
  0%   { left: -60%; }
  100% { left: 130%; }
}
/* Set animation-timing-function: linear */
```

---

## Used In
- [EnergyPoint/index.html](../index.html) — Hero section eyebrow badge
