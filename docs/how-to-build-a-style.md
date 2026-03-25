# How to Build a New Style Direction

This is the process for creating a new entry in the design-language gallery — a fully self-contained demo page that shows what a Storyteller story could feel like with a specific visual identity.

---

## Preferred method: Design Aesthetic Pipeline

The pipeline is the right way to build a new style. It runs 13 research and execution stages — typography, color, texture, motion, language, assets — and produces a deeply researched, fully executed demo. Brief goes in. Finished style comes out.

To start a pipeline run, fill out [`design-language/pipeline/brief-intake.md`](../design-language/pipeline/brief-intake.md) and hand it to Claude.

The quick prompt method below still works for fast experiments, but pipeline output is noticeably richer.

---

## What a Style Demo Is

Each style is a single HTML file that acts as a fake "issue" or "artifact" of a Storyteller story told in a specific aesthetic. It's not a UI mockup — it's a full-fidelity design exploration. A reader should feel immersed in the aesthetic within seconds.

The demo doesn't need to show product UI. It shows what the *world* of that style feels like. Think: if a newspaper existed in this universe, what would it look like? If a manuscript from this world washed ashore, what would you hold in your hands?

---

## Quick Method: Single Prompt

Paste this into a new Claude conversation to start a new style. Fill in the `[STYLE NAME]` and `[AESTHETIC DESCRIPTION]` before sending.

```
You are building a single-file HTML style demo for a project called Storyteller —
an AI-powered interactive fiction platform where users listen to stories and talk
back to them. Stories respond, remember, and adapt.

The demo should embody the aesthetic of: [STYLE NAME]

[AESTHETIC DESCRIPTION — e.g.: "A 1970s underground zine. Photocopied, lo-fi,
activist energy. Typefaces that look cut from other sources. Dense text.
Subversive tone."]

Build a self-contained, single-file HTML page (no external JS libraries, no
build tools). Embed all CSS and JS inline. Google Fonts are fine.

The page should:
1. Open with a powerful hero section that immediately establishes the aesthetic
2. Include 3–5 content sections that show how story content would be presented
   in this style (dialogue, scene-setting, choices, memory callbacks)
3. Feature at least one animation or interactive element that feels native to
   the aesthetic (not generic "scroll reveal")
4. End with a "back to gallery" link: href="./"
5. Optionally include a link to the main Storyteller site: href="../index.html"

The page is for a design gallery. It should look finished, not wireframey.
Every typographic and color choice should feel intentional.

Key constraints:
- No images (this is a code-only demo)
- No external dependencies beyond Google Fonts
- Works in modern browsers, no IE support needed
- Mobile-responsive is nice but not required
- The page should be dramatic. This is a creative showcase, not a documentation site.

After building, give me the complete HTML file.
```

---

## After Getting the File

1. Save it as `design-language/style-[kebab-name].html`
2. Test it locally — open in a browser, check all sections render
3. Add a card to `design-language/index.html` using the pattern of existing cards
4. Add a back-link: `<a href="./">← All Styles</a>` (should already be in the file from the prompt)
5. Commit with message: `feat: add [style name] style direction`

---

## Gallery Card Template

Find the right section in `design-language/index.html` (Foundations, Worlds, or Magazines) and add:

```html
<a href="style-your-name.html" class="style-card card-your-name" data-index="N">
  <div class="card-inner">
    <div class="card-preview card-preview-your-name">
      <div class="preview-content">
        <!-- 3–5 lines of flavor text from the style -->
      </div>
    </div>
    <div class="card-meta">
      <span class="card-tag">CATEGORY</span>
      <h3 class="card-title">Style Name</h3>
      <p class="card-desc">One sentence description of the aesthetic.</p>
    </div>
  </div>
</a>
```

Then add a CSS rule in the gallery's `<style>` block for `.card-preview-your-name` that visually distinguishes the card (background color, border treatment, etc.).

---

## Aesthetic Vocabulary

When writing the description for the prompt, these terms tend to produce good results:

- **Era** — 1920s, 1970s, near-future, timeless
- **Medium** — letterpress, broadcast, photocopied, illuminated manuscript, terminal
- **Tone** — austere, maximalist, cryptic, warm, clinical, reverent
- **Reference points** — specific publications, films, or art movements
- **Typography feel** — serif/sans ratio, tracking, weight contrast, leading
- **Color palette** — named colors or emotional descriptors ("aged paper and rust")

The more specific, the better. "Dark and mysterious" produces generic results. "A 1930s occult research journal, printed on cream stock, with dense footnotes and marginalia" produces something interesting.

---

## Current Styles

| File | Style |
|---|---|
| `style-primordial-fire.html` | Primordial Fire — elemental, ancient |
| `style-gutenberg-pulp.html` | Gutenberg Pulp — letterpress meets pulp fiction |
| `style-library-eternal.html` | Library Eternal — timeless archive |
| `style-infocom-terminal.html` | Infocom Terminal — classic text adventure |
| `style-oral-tradition.html` | Oral Tradition — campfire, spoken word |
| `style-dark-editorial.html` | Dark Editorial — high-contrast magazine |
| `style-manuscript.html` | Illuminated Manuscript — medieval sacred text |
| `style-void.html` | The Void — minimalist, cosmic silence |
| `style-risograph.html` | Risograph — indie print, limited color |
| `style-cartographer.html` | The Cartographer — hand-drawn maps, exploration |
| `style-neon-tokyo.html` | Neon Tokyo — cyberpunk, Japanese signage |
| `style-broadcast.html` | Broadcast — emergency alert, live feed |
| `style-vinyl.html` | Vinyl — record sleeve, analogue warmth |
| `style-cape-sorrow.html` | Cape Sorrow — gothic coastal noir |
| `style-giants.html` | Giants — myth, scale, ancient weight |
| `style-zeppelin-noir.html` | Zeppelin Noir — dieselpunk rain and shadow |
| `style-scriptorium.html` | Scriptorium — monastic stone and candlelight |
| `style-soviet.html` | Soviet — constructivist propaganda |
| `style-magazine-fashion.html` | Fashion Magazine — high editorial |
| `style-magazine-science.html` | Science Magazine — data-forward |
| `style-magazine-underground.html` | Underground Magazine — zine energy |
| `style-magazine-japan.html` | Japanese Magazine — layered, typographic |
| `style-magazine-longform.html` | Longform Magazine — literary, spacious |
| `style-magazine-tabloid.html` | Tabloid — sensational, dense |
