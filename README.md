# 2026-portfolio

Single-page editorial portfolio. No build step. You own everything — edit `index.html` directly, drop images into `images/`, push to GitHub.

## Run it locally

```bash
cd ~/Desktop/portfolio
python3 -m http.server 5173
# → http://localhost:5173/
```

The page auto-refreshes on hard reload (Cmd+Shift+R). No webpack, no nothing.

---

## How to edit the copy

Open [`index.html`](index.html) — every section is wrapped in a comment block like:

```html
<!-- ===========================================================
     03 SELECTED WORK  — EDIT: add/remove .card blocks
     =========================================================== -->
```

Find the section you want, change the text between the tags. That's it.

| Section | What's in it |
|---|---|
| **01 Index** | Your name, "Currently —" line, hero statement, 6 hero tiles, role/where/since |
| **02 Manifesto** | One philosophy paragraph + sign-off line |
| **03 Selected Work** | Project cards (drag/scroll/arrow-keys carousel) |
| **04 Shipping Log** | Milestones list — `name / sub / year` per row |
| **05 Writing** | Short numbered beliefs/notes |
| **06 Off the Clock** | 3 tiles + 2 personal paragraphs |
| **07 Contact** | Email + social links |
| **Footer** | Copyright + version tag |

Wrap any phrase in `<em>like this</em>` to make it serif-italic (Felix-style emphasis).
Wrap in `<strong>like this</strong>` for bold.

---

## How to add images

1. Drop your image into [`images/`](images/) — e.g. `images/uxie-hero.jpg`. JPGs/PNGs/WebPs all work. Aim for ~1200×900 px.
2. Reference it in `index.html`.

### Hero grid tiles (Section 01)
Replace the `<em>word</em>` with an `<img>`:

```html
<!-- before -->
<div class="cell"><span>01</span><em>voice</em></div>

<!-- after -->
<div class="cell"><span>01</span><em>voice</em><img src="images/voice.jpg" alt="Voice"></div>
```

The label stays on top with a subtle text shadow.

### Project cards (Section 03)
Replace the `.card-icon` glyph div with a `.card-media` block:

```html
<!-- before -->
<div class="card-icon">◉</div>

<!-- after -->
<div class="card-media"><img src="images/uxie-card.jpg" alt="Uxie"></div>
```

### Off-the-Clock tiles (Section 06)
Same pattern as hero cells:

```html
<div class="off-card"><span>3D</span><em>Blender + MCP</em><img src="images/blender.jpg" alt=""></div>
```

---

## How to change colors / fonts

Open [`styles.css`](styles.css). The top block is a CSS variable palette — change a value, both light and dark themes inherit it:

```css
html[data-theme="light"] {
  --paper: #f5f3ee;   /* background */
  --ink:   #14130f;   /* text */
  --muted: #807d74;   /* secondary text */
  --line:  #d9d6cd;   /* borders */
  ...
}
html[data-theme="dark"] { ... }
```

Fonts come from Google Fonts — see the `<link>` tag in `<head>`.

---

## Publish your changes

```bash
cd ~/Desktop/portfolio
git add .
git commit -m "Update copy + add hero images"
git push
```

The repo is at https://github.com/Ronda1723/2026-portfolio.

---

## Deploy live (optional)

Easiest path — **Vercel**:

```bash
npx vercel --prod
```

Or push the repo to **Vercel** / **Netlify** via their dashboards — no config needed, the site is pure HTML/CSS. GitHub Pages also works from the repo settings.

---

## Anatomy

```
portfolio/
├── index.html      ← all copy lives here, marked with EDIT comments
├── styles.css      ← theme palette + layout
├── images/         ← drop your photos here
└── README.md       ← this file
```

That's the whole thing.
