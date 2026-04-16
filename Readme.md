# Lonjezo Chingayipe — Developer Portfolio

Personal portfolio website built as a static single-page application, hosted on GitHub Pages.

**Live site:** [lonjezano.github.io](https://lonjezano.github.io)

---

## Stack

| Tool | Purpose |
|------|---------|
| [Tailwind CSS v4](https://tailwindcss.com) | Utility-first styling, compiled locally via CLI |
| [Alpine.js v3](https://alpinejs.dev) | Reactivity, section filtering, scroll tracking |
| [@alpinejs/intersect](https://alpinejs.dev/plugins/intersect) | Scroll-triggered reveal animations |
| [Google Fonts](https://fonts.google.com) | Syne (display) · JetBrains Mono (mono) · Lora (body) |

No build framework. No bundler. Just a compiled CSS file and a single HTML file.

---

## Project Structure

```
portfolio/
├── index.html          # Single-page application
├── app.css             # Tailwind source + custom theme (@theme)
├── styles.css          # Compiled output — generated, do not edit manually
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

---

## Local Development

### Prerequisites

- Node.js v18+ (uses nvm: `nvm use 24`)
- npm v9+

### Install dependencies

```bash
npm install
```

### Watch mode (auto-recompile on save)

```bash
npm run dev
```

Open `index.html` directly in your browser. Refresh after saving changes.

### Production build

```bash
npm run build
```

This scans `index.html`, extracts all used Tailwind classes, and outputs a minified `styles.css`.

---

## Deployment

This site deploys to GitHub Pages from the `main` branch root.

### First-time setup

```bash
git init
git add .
git commit -m "Initial portfolio"
git branch -M main
git remote add origin https://github.com/Lonjezano/Lonjezano.github.io.git
git push -u origin main
```

Then go to: **GitHub repo → Settings → Pages → Source → main branch → / (root) → Save**

Live within ~60 seconds at `https://lonjezano.github.io`.

### Pushing updates

Always rebuild CSS before committing if you changed any Tailwind classes:

```bash
npm run build
git add index.html styles.css
git commit -m "Update portfolio"
git push
```

---

## Customisation

### Updating content

All content (experience, projects, skills, facts) lives in the `portfolio()` JavaScript function at the bottom of `index.html`. Edit the data arrays directly — no separate data files.

### Updating the theme

Custom colours and fonts are defined in `app.css` under `@theme`. After any change, run `npm run build` to recompile.

### Adding a new section

1. Add a `<section id="new-section">` block in `index.html`
2. Add `{ id: 'new-section', label: 'Label' }` to the `sections` array in `portfolio()`
3. Rebuild CSS

---

## Sections

| # | Section | Description |
|---|---------|-------------|
| 01 | Hero | Name, role, positioning statement, CTA buttons |
| 02 | About | Bio, quick stats (years, systems shipped, languages) |
| 03 | Skills | Grouped by category with hover effects |
| 04 | Experience | Timeline of work history with bullet achievements |
| 05 | Projects | Filterable cards (Professional / Academic / Personal) |
| 06 | Contact | Email, LinkedIn, GitHub links |

---

## Notes

- `styles.css` is committed intentionally — GitHub Pages is static and needs the compiled file
- `node_modules/` is gitignored
- Alpine.js and the Intersect plugin are loaded via CDN ESM imports — no bundler required
- The site works fully offline once loaded (except Google Fonts)