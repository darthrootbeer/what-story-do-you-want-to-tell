# What Story Do You Want to Tell?

Public-facing site for the **Storyteller** project — an interactive fiction platform where stories talk back.

Live at: [darthrootbeer.github.io/what-story-do-you-want-to-tell](https://darthrootbeer.github.io/what-story-do-you-want-to-tell/)

---

## Site Structure

```
/
├── index.html                  Landing page ("Stories have always been alive.")
│
├── phase-1-vision/             Concept page — what Storyteller is, emotionally
├── phase-1-overview/           Plain-English overview of Phase 1
├── phase-1-technical/          Full technical deep-dive
│
├── assets/                     Images and SVGs used by the live site
├── 404.html                    GitHub Pages 404
└── README.md                   This file
```

> **Design language work** (style demos, aesthetic pipeline) lives in the private repo: [darthrootbeer/storyteller-design-language](https://github.com/darthrootbeer/storyteller-design-language)

---

## The Visitor Flow

The phase-1 pages form a single linear narrative:

```
index.html  →  phase-1-overview/  →  phase-1-technical/
```

---

## Building

No build tools. No dependencies. Every page is a self-contained `.html` file with embedded CSS and JS.

To work on the site locally, just open any `.html` file in a browser.

To publish, push to `master` — GitHub Pages deploys automatically from the root.

---

## Contributing

All pages are self-contained `.html` files with inline CSS and JS. No build tools, no dependencies. Open any file in a browser to preview locally. Push to `master` to deploy.
