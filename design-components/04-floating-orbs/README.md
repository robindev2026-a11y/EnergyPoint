# 04 — Floating Energy Orbs

**Category:** Background / Ambient Animation  
**Complexity:** ⭐ Easy  
**Dependencies:** None — Pure CSS

---

## What It Is

Large, blurred radial gradient circles positioned absolutely in the background. They drift slowly using `@keyframes` with `translate` + `scale` transforms. Creates a sense of depth, atmosphere, and movement without any JavaScript.

---

## When To Use

- Hero backgrounds (works great alongside particle canvas)
- Section backgrounds for visual interest
- Login/onboarding pages
- Any place you want to add depth to a flat dark background

---

## HTML

```html
<div class="hero" style="position: relative; overflow: hidden;">
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>
  
  <div class="hero-content" style="position: relative; z-index: 1;">
    <!-- your content -->
  </div>
</div>
```

---

## CSS

```css
/* Base orb style */
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);       /* Heavy blur = soft glow */
  pointer-events: none;
  z-index: 0;
}

/* Orb 1 — Large cyan, top right */
.orb-1 {
  width: 500px; height: 500px;
  background: radial-gradient(circle, rgba(0,229,255,0.08) 0%, transparent 70%);
  top: -200px; right: -100px;
  animation: orb-drift-1 14s ease-in-out infinite;
}

/* Orb 2 — Medium lime, bottom left */
.orb-2 {
  width: 380px; height: 380px;
  background: radial-gradient(circle, rgba(57,255,20,0.06) 0%, transparent 70%);
  bottom: 50px; left: 10%;
  animation: orb-drift-2 18s ease-in-out infinite;
}

/* Orb 3 — Small cyan, center */
.orb-3 {
  width: 280px; height: 280px;
  background: radial-gradient(circle, rgba(0,229,255,0.05) 0%, transparent 70%);
  top: 40%; left: 40%;
  animation: orb-drift-3 22s ease-in-out infinite;
}

/* Each orb has a unique drift pattern */
@keyframes orb-drift-1 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33%  { transform: translate(-30px, 40px) scale(1.05); }
  66%  { transform: translate(20px, -20px) scale(0.95); }
}
@keyframes orb-drift-2 {
  0%, 100% { transform: translate(0, 0); }
  50%  { transform: translate(40px, -50px); }
}
@keyframes orb-drift-3 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  40%  { transform: translate(-25px, 30px) scale(1.1); }
  80%  { transform: translate(15px, -20px) scale(0.9); }
}
```

---

## How It Works

1. Each orb is a `div` with a **radial gradient** from a color to `transparent`
2. `filter: blur(80px)` makes them huge and soft — no hard edges
3. Very low opacity (0.05–0.08) keeps them subtle
4. Each has a **unique keyframe animation** with different duration (14s, 18s, 22s)
5. Different durations prevent them from syncing up — they feel organic

---

## Customization

| Property | How |
|---|---|
| Color | Change `rgba(0,229,255,...)` |
| Intensity | Increase the opacity value (0.08 → 0.15) |
| Blur amount | Change `blur(80px)` — more blur = larger, softer |
| Speed | Change animation durations (14s, 18s, 22s) |
| Size | Change `width/height` values |
| Position | Adjust `top/bottom/left/right` |
| Add more orbs | Duplicate with a new animation keyframe |

---

## Used In
- [EnergyPoint/index.html](../index.html) — Hero section background
