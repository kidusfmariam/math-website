# Wandering Sailboat's Math Journey

A minimal personal site for logging a self-directed study of pure mathematics.

---

## File structure

```
sailboat-math/
├── index.html              ← The public site (course list only)
├── admin.html              ← YOUR PRIVATE TOOL — never push this to GitHub
├── .gitignore              ← Excludes admin.html from Git
├── README.md               ← This file
└── notes/
    ├── mathematical-logic.html    ← Your first course (replace with real notes)
    └── (add more here as you go)
```

---

## Deploying to GitHub Pages

1. Create a new GitHub repository (e.g. `math-journey`)
2. Upload all files in this folder to the repo
3. Go to **Settings → Pages**, set source to `main` branch, root `/`
4. Your site will be live at `https://yourusername.github.io/math-journey/`

---

## Adding a new course's notes

### Step 1 — Convert your PDF (privately, on your machine)

1. Open `admin.html` locally in your browser (just double-click the file)
2. Drag your PDF onto the upload zone (or click to browse)
3. A `.html` file will download automatically (e.g. `axiomatic-set-theory.html`)
4. Move it into the `notes/` folder

### Step 2 — Add it to the course list in `index.html`

Find the planned `<li>` entry for that course and change it from this:

```html
<li class="course-item planned">
  <div class="course-row">
    <span class="course-name">Axiomatic Set Theory</span>
    <span class="course-status">Planned</span>
  </div>
</li>
```

To this:

```html
<li class="course-item done">
  <a href="notes/axiomatic-set-theory.html">
    <span class="course-name">Axiomatic Set Theory</span>
    <span class="course-status">Completed</span>
  </a>
</li>
```

### Step 3 — Push to GitHub

Commit and push both the new notes file and the updated `index.html`.

---

## Notes on PDF conversion

The uploader converts text-based PDFs in the browser using PDF.js, then wraps the
output in a page that renders LaTeX math with MathJax.

**Works well for:** PDFs exported directly from LaTeX (e.g. pdflatex output)

**May struggle with:** Scanned PDFs, or PDFs where math is embedded as images rather
than text. For those, consider running your `.tex` source through
[Pandoc](https://pandoc.org/) to produce HTML directly:

```bash
pandoc your-notes.tex -o notes/course-name.html --mathjax --standalone
```

This gives the cleanest result since it works from the source, not the PDF.
