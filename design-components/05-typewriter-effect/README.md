# 05 — Typewriter Text Effect

**Category:** Animation / Typography  
**Complexity:** ⭐⭐ Medium  
**Dependencies:** None — Pure Vanilla JS

---

## What It Is

A classic typewriter effect that reveals text character by character. Supports:
- **Line breaks** via `\n` in the string (converts to `<br>`)
- **Blinking cursor** that fades out when typing finishes
- **Variable speed** — starts slightly slower, speeds up

---

## When To Use

- Hero headlines for strong first impression
- Terminal / code-themed UIs
- Taglines that you want users to "read along with"
- After a loading screen completes (pair with the loader component)

---

## HTML

```html
<h1>
  <span id="hero-text"></span>
  <span class="typewriter-cursor" id="hero-cursor"></span>
</h1>
```

---

## CSS

```css
.typewriter-cursor {
  display: inline-block;
  width: 3px;
  height: 0.85em;
  background: #00e5ff;          /* cursor color */
  margin-left: 4px;
  vertical-align: middle;
  border-radius: 2px;
  animation: blink-cursor 0.8s step-end infinite;
}

@keyframes blink-cursor {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0; }
}
```

---

## JavaScript

```js
function startTypewriter() {
  // Use \n for line breaks — they become <br> tags
  const text   = 'THE FUTURE\nOF ENERGY\nSTORAGE.';
  const el     = document.getElementById('hero-text');
  const cursor = document.getElementById('hero-cursor');
  let idx = 0;

  const type = () => {
    if (idx < text.length) {
      const ch = text[idx];
      if (ch === '\n') {
        el.innerHTML += '<br>';
      } else {
        el.innerHTML += ch;
      }
      idx++;
      // Slightly slower for first 10 chars, then faster
      setTimeout(type, idx < 10 ? 55 : 38);
    } else {
      // Done typing — fade cursor out after 2.2 seconds
      setTimeout(() => { cursor.style.opacity = '0'; }, 2200);
    }
  };

  type(); // Start!
}

// Call this when you want typing to begin
// e.g., after the page loader completes:
startTypewriter();
```

---

## How It Works

1. The text string stores `\n` for line breaks
2. A recursive `setTimeout` function processes one character per call
3. If the character is `\n`, it appends `<br>` to the DOM instead of the literal character
4. Otherwise, it appends the character directly to `innerHTML`
5. `idx < 10` check makes the first 10 characters slightly slower — feels more natural
6. On completion, the cursor element fades out with `opacity: 0`

---

## Customization

| Property | Where |
|---|---|
| Text content | Change the `text` string |
| Typing speed | Change `55` (slow) and `38` (fast) ms values |
| Cursor color | `background: #00e5ff` in `.typewriter-cursor` |
| Cursor blink | `animation: blink-cursor 0.8s` — change `0.8s` |
| Cursor shape | Change `width`, `height`, `border-radius` |
| Keep cursor visible | Remove the `setTimeout(...opacity = '0'...)` call |

---

## Variants

**Faster, no slowdown:**
```js
setTimeout(type, 40); // constant 40ms
```

**Delete and retype loop:**
```js
// After typing forward, decrement idx and delete characters
// Then increment and retype for a loop effect
```

---

## Used In
- [EnergyPoint/index.html](../index.html) — Hero headline
