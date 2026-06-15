# 12 — Scroll Reveal Animation

**Category:** Animation / Layout  
**Complexity:** ⭐ Easy  
**Dependencies:** IntersectionObserver (all modern browsers)

---

## What It Is

Elements **fade in and slide up** (or from sides) as they scroll into the viewport. Uses `IntersectionObserver` — no `scroll` event listener, no GSAP required.

Three variants:
- `.reveal` — fade in + slide up (most common)
- `.reveal-left` — fade in + slide from left
- `.reveal-right` — fade in + slide from right

**Stagger delays** (`.reveal-delay-1` through `.reveal-delay-6`) let sibling items cascade in.

---

## When To Use

- Benefit/feature cards
- Section headings
- Any content that appears below the fold
- Gives a site a polished, "alive" feeling without complex libraries

---

## HTML

```html
<!-- Basic reveal -->
<h2 class="reveal">Why Lithium beats traditional batteries.</h2>

<!-- Reveal from sides (for two-column layouts) -->
<div class="reveal-left">Left column content</div>
<div class="reveal-right">Right column content</div>

<!-- Staggered card grid -->
<div class="cards-grid">
  <div class="card reveal reveal-delay-1">Card 1</div>
  <div class="card reveal reveal-delay-2">Card 2</div>
  <div class="card reveal reveal-delay-3">Card 3</div>
  <div class="card reveal reveal-delay-4">Card 4</div>
</div>
```

---

## CSS

```css
/* ─── Base states (hidden) ─────────────── */
.reveal {
  opacity: 0;
  transform: translateY(32px);
  transition:
    opacity  0.7s cubic-bezier(0.23, 1, 0.32, 1),
    transform 0.7s cubic-bezier(0.23, 1, 0.32, 1);
}
.reveal-left {
  opacity: 0;
  transform: translateX(-32px);
  transition:
    opacity  0.7s cubic-bezier(0.23, 1, 0.32, 1),
    transform 0.7s cubic-bezier(0.23, 1, 0.32, 1);
}
.reveal-right {
  opacity: 0;
  transform: translateX(32px);
  transition:
    opacity  0.7s cubic-bezier(0.23, 1, 0.32, 1),
    transform 0.7s cubic-bezier(0.23, 1, 0.32, 1);
}

/* ─── Revealed state (JS adds this class) ─ */
.reveal.revealed,
.reveal-left.revealed,
.reveal-right.revealed {
  opacity: 1;
  transform: translate(0, 0);
}

/* ─── Stagger delays ───────────────────── */
.reveal-delay-1 { transition-delay: 0.08s; }
.reveal-delay-2 { transition-delay: 0.16s; }
.reveal-delay-3 { transition-delay: 0.24s; }
.reveal-delay-4 { transition-delay: 0.32s; }
.reveal-delay-5 { transition-delay: 0.40s; }
.reveal-delay-6 { transition-delay: 0.48s; }
```

---

## JavaScript

```js
function initScrollReveal() {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('revealed');
        observer.unobserve(entry.target); // Animate only once
      }
    });
  }, {
    threshold: 0.12,              // Trigger when 12% of element is visible
    rootMargin: '0px 0px -40px 0px'  // -40px from bottom = triggers slightly earlier
  });

  // Observe all three variants
  document.querySelectorAll('.reveal, .reveal-left, .reveal-right')
    .forEach(el => observer.observe(el));
}

initScrollReveal();
```

---

## How It Works

1. All `.reveal` elements start **invisible and translated** (hidden below view)
2. `IntersectionObserver` watches them without any scroll event overhead
3. When 12% of the element enters the viewport, `.revealed` is added
4. The CSS `transition` smoothly animates to `opacity: 1, transform: none`
5. `observer.unobserve()` ensures each element only animates once (not on scroll back up)
6. `transition-delay` classes create a **cascade/stagger** when multiple items share the same `IntersectionObserver` entry (e.g., cards in a grid)

---

## Customization

| Property | Where |
|---|---|
| Slide distance | Change `32px` in the base `transform` |
| Duration | Change `0.7s` in `transition` |
| Trigger point | Change `threshold` (0.12 = 12% visible) |
| Root margin | Change `-40px` to trigger later/earlier |
| Easing | Change `cubic-bezier(0.23, 1, 0.32, 1)` (current = "ease-out spring") |
| More stagger steps | Add `.reveal-delay-7 { transition-delay: 0.56s; }` etc. |
| Re-animate on scroll-up | Remove `observer.unobserve(entry.target)` |

---

## Used In
- [EnergyPoint/index.html](../index.html) — All sections, cards, headings
