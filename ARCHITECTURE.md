# Architecture

How this site is built and how to extend it.

---

## Philosophy

Every page is a single self-contained `.html` file. No build tools, no frameworks, no dependencies. All CSS and JavaScript lives inline in each file.

This is intentional. The pages are meant to be dense, immersive, and independently deployable. Anyone can clone this repo and open a file in a browser — nothing to install.

---

## Page Anatomy

A typical page has three sections in the `<head>`:

1. **Fonts** — loaded from Google Fonts via `<link>`
2. **CSS** — all styles inline in a `<style>` block
3. **Meta** — standard viewport, charset, title

The body contains semantic HTML sections, followed by a `<script>` block at the end with all JavaScript.

---

## Animation Patterns

### Scroll Reveal

Most content sections use `IntersectionObserver` to trigger a `.revealed` class as they enter the viewport. The CSS defines the initial (hidden) and final (visible) states; JS adds the class.

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('revealed');
  });
}, { threshold: 0.15 });

document.querySelectorAll('.reveal-target').forEach(el => observer.observe(el));
```

### Typewriter Effect

Used on the hero text. Characters are appended one at a time with `setTimeout`, with per-character jitter for a natural feel.

```js
function typeWriter(el, text, speed, jitter) {
  let i = 0;
  function typeNext() {
    el.textContent += text[i++];
    if (i < text.length) setTimeout(typeNext, speed + (Math.random() * jitter * 2 - jitter));
  }
  setTimeout(typeNext, delay);
}
```

Key detail: set `opacity: 0` in CSS, add `.typing` class (which sets `opacity: 1`) in JS before the first character is appended. This prevents a flash of content before JS runs.

### Word-by-Word Blur Materialize

Used on "STORIES TALK BACK." Each word starts blurred and transitions to sharp. Stagger timing with `setTimeout` per word.

```css
.word { filter: blur(18px); opacity: 0; transition: filter 1.8s ease, opacity 1.8s ease; }
.word.visible { filter: blur(0); opacity: 1; }
```

### Strikethrough Draw

Used in the "What it isn't" list. An absolutely-positioned `::after` pseudo-element starts at `width: 0` and transitions to `width: 100%`, drawing left-to-right.

```css
.strikethrough-text { position: relative; display: inline; }
.strikethrough-text::after {
  content: '';
  position: absolute;
  left: 0; top: 0.85em;
  width: 0; height: 4px;
  background: currentColor;
  transition: width 3s ease;
  transform: rotate(-0.8deg);
}
.struck .strikethrough-text::after { width: 100%; }
```

---

## Asset Paths

All images and SVGs live in `/assets/`. Pages reference them with paths relative to their own location.

| Page location | Relative path to assets |
|---|---|
| Root (`index.html`) | `assets/filename.png` |
| One level deep (`phase-1-overview/index.html`) | `../assets/filename.png` |
| `design-language/style-*.html` | `../assets/filename.png` (if needed) |

---

## Navigation

The site has two separate navigation clusters that do not cross-link:

**Phase 1 visitor flow:**
```
index.html → phase-1-overview/ → phase-1-technical/
```

**Design language (internal / creative sandbox):**
```
design-language/index.html → design-language/style-*.html
```

The `styles-gallery.html` file at root is a legacy redirect stub pointing to `design-language/`.

---

## Adding a New Page to the Visitor Flow

1. Create a new folder: `mkdir new-page-name/`
2. Create `new-page-name/index.html`
3. Asset paths use `../assets/`
4. Back-link to root: `href="../index.html"`
5. Add forward/back links in the adjacent pages that should connect to it

---

## Hosting

GitHub Pages, deployed automatically from the `master` branch root.

The site URL is: `https://darthrootbeer.github.io/what-story-do-you-want-to-tell/`

Folder-based pages (e.g. `phase-1-overview/index.html`) are accessible at clean URLs like `.../phase-1-overview/` — no `.html` extension needed.
