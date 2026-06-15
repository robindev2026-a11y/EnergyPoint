# 13 — Nav Blur on Scroll

**Category:** Navigation / UI Polish  
**Complexity:** ⭐ Easy  
**Dependencies:** None — Pure CSS + Vanilla JS

---

## What It Is

A navigation bar that **starts transparent** (so it blends with the hero) and gains a **frosted glass blur background** as the user scrolls down. A single JavaScript scroll listener adds/removes a CSS class — all visual changes are handled by CSS transitions.

---

## When To Use

- Any site with a full-screen hero behind the nav
- Landing pages where the hero and nav share the same background
- Creates a premium feel — the nav "materializes" as you scroll

---

## HTML

```html
<nav id="main-nav">
  <!-- nav content -->
</nav>
```

---

## CSS

```css
/* Default state — fully transparent */
#main-nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 50;
  
  background: rgba(5, 7, 15, 0);       /* fully transparent */
  backdrop-filter: blur(0px);           /* no blur */
  border-bottom: 1px solid rgba(255, 255, 255, 0);  /* invisible border */
  
  /* Smooth transition for all properties */
  transition:
    background    0.4s ease,
    backdrop-filter 0.4s ease,
    border-color  0.4s ease;
}

/* Scrolled state — glass effect activates */
#main-nav.scrolled {
  background: rgba(5, 7, 15, 0.85);    /* 85% opaque dark */
  backdrop-filter: blur(24px);          /* strong blur */
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);  /* subtle separator */
}
```

---

## JavaScript

```js
function initNavBlur() {
  const nav = document.getElementById('main-nav');
  
  window.addEventListener('scroll', () => {
    // Add 'scrolled' class once user scrolls past 40px
    nav.classList.toggle('scrolled', window.scrollY > 40);
  });
}

initNavBlur();
```

---

## How It Works

1. Nav starts with `background: rgba(..., 0)` and `backdrop-filter: blur(0px)` — effectively invisible
2. `window.addEventListener('scroll', ...)` fires on every scroll event
3. `classList.toggle('scrolled', condition)` adds the class when `scrollY > 40`, removes it when not
4. CSS `transition` smoothly animates between the two states over 0.4s
5. `backdrop-filter: blur(24px)` creates the frosted glass effect on the `.scrolled` state

> [!NOTE]
> `backdrop-filter` requires content behind the nav to be visible. Works perfectly when nav is `position: fixed` over a page.

---

## Customization

| Property | Where |
|---|---|
| Scroll trigger point | Change `40` in `window.scrollY > 40` |
| Background opacity | Change `0.85` in `.scrolled` background |
| Blur amount | Change `24px` in `.scrolled` backdrop-filter |
| Transition speed | Change `0.4s` |
| Border visibility | Change `0.08` opacity in `.scrolled` border |

---

## Used In
- [EnergyPoint/index.html](../index.html) — Main navigation
