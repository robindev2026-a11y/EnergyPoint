# 08 — Tech Feature Marquee Strip

**Category:** UI Component / Animation  
**Complexity:** ⭐⭐ Medium  
**Dependencies:** None — Pure CSS animation

---

## What It Is

An infinitely scrolling horizontal marquee of **pill-shaped feature tags**. Uses pure CSS animation — no JavaScript.

Key features:
- Two copies of the content scroll in sequence (creates seamless loop)
- **Pauses on hover** (`animation-play-state: paused`)
- Edges fade out with a CSS `mask-image`
- Each pill has a colored dot indicator and hover effect

---

## When To Use

- Technology / features strip
- Brand logos row
- "Works with" integrations
- Social proof badges
- Any list of items too long to show statically

---

## HTML

```html
<div class="marquee-track">
  <!-- COPY 1 -->
  <div class="marquee-content">
    <div class="tech-pill"><div class="pill-dot dot-cyan"></div>BMS Protected</div>
    <div class="tech-pill"><div class="pill-dot dot-lime"></div>LFP Chemistry</div>
    <div class="tech-pill"><div class="pill-dot dot-cyan"></div>App Connected</div>
    <div class="tech-pill"><div class="pill-dot dot-lime"></div>6000+ Cycles</div>
    <div class="tech-pill"><div class="pill-dot dot-cyan"></div>Solar Ready</div>
    <!-- add more pills... -->
  </div>
  <!-- COPY 2 — identical, aria-hidden for accessibility -->
  <div class="marquee-content" aria-hidden="true">
    <!-- same pills repeated -->
  </div>
</div>
```

---

## CSS

```css
/* Outer container — clips overflow and fades edges */
.marquee-track {
  display: flex;
  overflow: hidden;
  /* Fade edges to transparent */
  mask-image: linear-gradient(
    to right,
    transparent 0%,
    black 10%,
    black 90%,
    transparent 100%
  );
  -webkit-mask-image: linear-gradient(
    to right,
    transparent 0%,
    black 10%,
    black 90%,
    transparent 100%
  );
}

/* Each copy scrolls independently */
.marquee-content {
  display: flex;
  gap: 1rem;
  flex-shrink: 0;        /* Don't wrap */
  animation: marquee-scroll 28s linear infinite;
}

/* Second copy starts halfway through for seamless loop */
.marquee-content:nth-child(2) {
  animation-delay: -14s; /* Half of 28s */
}

@keyframes marquee-scroll {
  0%   { transform: translateX(0); }
  100% { transform: translateX(-100%); }
}

/* Pause on hover */
.marquee-track:hover .marquee-content {
  animation-play-state: paused;
}

/* Individual pill */
.tech-pill {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1.2rem;
  border-radius: 99px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(255, 255, 255, 0.03);
  font-size: 0.8rem;
  white-space: nowrap;
  cursor: default;
  transition: border-color 0.3s, background 0.3s, transform 0.3s;
}

.tech-pill:hover {
  border-color: rgba(0, 229, 255, 0.4);
  background: rgba(0, 229, 255, 0.06);
  transform: translateY(-2px);
}

/* Dot colors */
.pill-dot {
  width: 6px; height: 6px; border-radius: 50%;
}
.dot-cyan { background: #00e5ff; }
.dot-lime { background: #39ff14; }
```

---

## How It Works

1. Two `.marquee-content` divs sit side by side inside `.marquee-track`
2. Both animate `translateX(0 → -100%)` — moving left by their full width
3. The second copy starts at `-14s` delay (half the 28s duration) → they never both disappear at once
4. When the first copy has moved off-screen left (`-100%`), the second one has moved into exactly the same position as the first copy started → **seamless loop**
5. `mask-image` fades the left/right 10% to transparent — hides the seams

---

## Customization

| Property | Where |
|---|---|
| Speed | Change `28s` in animation — lower = faster |
| Gap between pills | Change `gap: 1rem` in `.marquee-content` |
| Fade width | Change `10%` in `mask-image` |
| Direction (right-to-left) | Default. For L→R: `translateX(0 → 100%)` and start at `100%` |
| Pause on hover | Remove `.marquee-track:hover` rule to disable |

---

## Used In
- [EnergyPoint/index.html](../index.html) — Technology strip section
