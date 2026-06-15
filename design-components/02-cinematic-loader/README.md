# 02 — Cinematic Loading Screen

**Category:** Animation / Entry Experience  
**Complexity:** ⭐⭐ Medium  
**Dependencies:** None — Pure CSS + Vanilla JS

---

## Preview

![Cinematic Loader](./screenshot.png)

*Progress bar fills with staged label changes: INITIALIZING → LOADING → CALIBRATING → READY*

---

## What It Is

A full-screen overlay that covers the page during initial load. Features:
- **Branded logo badge** with a pulse animation
- **Staged progress bar** that fills with randomized tick steps
- **Dynamic status labels** that change as progress crosses thresholds
- **Smooth fade-out** when complete — then triggers hero entrance animations

---

## When To Use

- Premium product/brand websites
- Portfolio launches
- Apps with real loading (assets, API calls)
- Creates a great first impression and buys time for fonts/images to load

---

## HTML

```html
<!-- Place as very first child of <body> -->
<div id="loader">
  <div class="loader-logo">EP</div>
  <div class="loader-brand-name">ENERGYPOINT</div>
  <div class="loader-bar-track">
    <div class="loader-bar-fill" id="loader-bar"></div>
  </div>
  <div class="loader-label" id="loader-label">INITIALIZING…</div>
</div>
```

---

## CSS

```css
#loader {
  position: fixed; inset: 0; z-index: 9999;
  background: #05070f;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  transition: opacity 0.7s ease, visibility 0.7s ease;
}
#loader.hidden {
  opacity: 0; visibility: hidden; pointer-events: none;
}

.loader-logo {
  width: 56px; height: 56px; border-radius: 1rem;
  background: linear-gradient(135deg, #00e5ff, #39ff14);
  display: flex; align-items: center; justify-content: center;
  font-weight: 700; font-size: 1.5rem; color: #05070f;
  margin-bottom: 1.5rem;
  animation: loader-pulse 1s ease-in-out infinite;
}
@keyframes loader-pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(0,229,255,0.4); }
  50% { box-shadow: 0 0 0 16px rgba(0,229,255,0); }
}

.loader-brand-name {
  font-size: 0.7rem; letter-spacing: 0.25em;
  color: rgba(255,255,255,0.4); font-weight: 500;
}

.loader-bar-track {
  width: 160px; height: 2px;
  background: rgba(255,255,255,0.1);
  border-radius: 99px; overflow: hidden; margin-top: 1rem;
}
.loader-bar-fill {
  height: 100%; width: 0%;
  background: linear-gradient(to right, #00e5ff, #39ff14);
  border-radius: 99px;
  transition: width 0.05s linear;
}
.loader-label {
  margin-top: 0.75rem; font-size: 0.65rem;
  letter-spacing: 0.2em; color: rgba(255,255,255,0.35);
  font-family: monospace;
}
```

---

## JavaScript

```js
(function initLoader() {
  const loader = document.getElementById('loader');
  const bar    = document.getElementById('loader-bar');
  const label  = document.getElementById('loader-label');

  // Customize these labels for your brand
  const labels = ['INITIALIZING…', 'LOADING ASSETS…', 'CALIBRATING…', 'CHARGING…', 'READY'];
  let progress = 0, labelIdx = 0;

  const tick = setInterval(() => {
    // Random increment between 8–30 per tick
    progress += Math.random() * 22 + 8;
    if (progress >= 100) progress = 100;
    bar.style.width = progress + '%';

    // Update label at 25% intervals
    const lIdx = Math.min(Math.floor(progress / 25), labels.length - 1);
    if (lIdx !== labelIdx) { labelIdx = lIdx; label.textContent = labels[labelIdx]; }

    if (progress >= 100) {
      clearInterval(tick);
      label.textContent = 'READY';
      setTimeout(() => {
        loader.classList.add('hidden');
        // 🔥 Trigger your hero entrance animations here
        onLoaderComplete();
      }, 300);
    }
  }, 80); // Tick every 80ms
})();

function onLoaderComplete() {
  // Start typewriter, reveal animations, etc.
  console.log('Loader complete — start hero animations');
}
```

---

## How It Works

1. A `setInterval` runs every **80ms**, adding a random amount (8–30) to progress
2. Randomness creates a natural-feeling "loading" (not perfectly linear)
3. At **100%**, the interval clears and a `setTimeout(300ms)` triggers fade-out via adding `.hidden`
4. CSS `transition: opacity 0.7s, visibility 0.7s` handles the smooth disappear
5. `onLoaderComplete()` is your hook to fire post-load animations

---

## Customization

| Property | Where |
|---|---|
| Background color | `#loader { background: ... }` |
| Logo text / badge | Change inner HTML of `.loader-logo` |
| Stage labels | Edit the `labels` array |
| Speed | Change `80` (interval ms) and `22 + 8` (range) |
| Fade duration | `transition: opacity 0.7s` in `#loader.hidden` |
| Bar colors | `.loader-bar-fill { background: ... }` |

---

## Used In
- [EnergyPoint/index.html](../index.html)
