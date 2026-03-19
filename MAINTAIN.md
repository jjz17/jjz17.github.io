# Maintenance Guide

> For human developers and Claude Code alike — everything you need to maintain, update, and extend this portfolio site.

---

## Architecture Overview

This is a **zero-build, single-page portfolio** with a strict separation between content and presentation.

```
index.html            ← Layout, styling, Alpine.js logic (the "engine")
data/portfolio.json   ← All content (the "fuel")
assets/               ← Static files (CV PDF, images, etc.)
```

**Data flow:** On page load, the Alpine.js `portfolio()` function calls `fetch('data/portfolio.json')`, populates the reactive `d` object, and Alpine renders every section via `x-for`, `x-text`, and `x-html` directives. After render, `lucide.createIcons()` is called via `$nextTick` to initialize any dynamically inserted icons.

**Key libraries (all loaded via CDN — no npm, no build):**

| Library | Purpose | Loaded via |
|---|---|---|
| Tailwind CSS | Utility-first styling + dark mode (`dark:` variant) | `<script src="https://cdn.tailwindcss.com">` |
| Alpine.js 3.x | Reactivity, data binding, template rendering | `<script defer>` — must be deferred |
| Lucide Icons | SVG icons referenced by name in JSON | `<script src="https://unpkg.com/lucide@latest">` |
| Google Fonts | Playfair Display (headings) + Inter (body) | `<link>` preconnect |

---

## The Golden Rule

**To update content, only edit `data/portfolio.json`. Never touch `index.html` for content changes.**

Only modify `index.html` when:
- Adding a new **section type** (new visual layout)
- Changing **design/styling** (CSS, Tailwind classes)
- Adding new **interactive behavior** (Alpine.js logic)
- Modifying the **Tailwind config** (colors, fonts, breakpoints)

---

## File Reference

### `index.html` Structure (top to bottom)

| Lines (approx.) | Region | Purpose |
|---|---|---|
| 1–41 | `<head>` config | Meta tags, font imports, Tailwind config (colors, fonts) |
| 42–52 | CDN scripts | Alpine.js (deferred), Lucide Icons |
| 57–137 | `<style>` block | Custom CSS: dot-grid, glassmorphism, timeline, hover-lift, fade-section, heatmap, pipeline connectors, skeleton pulse |
| 150–159 | Loading state | Spinner shown while JSON loads (`x-if="!loaded"`) |
| 164–596 | Main content | All sections wrapped in `<template x-if="loaded">` |
| 170–215 | Navbar | Glassmorphism sticky nav, mobile hamburger, dark mode toggle |
| 220–254 | Hero | Name, tagline, social links |
| 260–275 | Experience | Timeline with `x-for="(job, i) in d.experience"` |
| 281–299 | Education | List with graduation cap icons |
| 305–332 | Projects | Card grid with icon, impact badge, tools, GitHub link |
| 339–390 | Publications | Color-coded cards (paper=indigo, talk=emerald), TL;DR |
| 397–445 | Methodology | Interactive pipeline — click to expand detail panel |
| 451–467 | Stack | Skills grouped by category |
| 472–506 | Reading + Metrics | Book widget with progress bar, metric counters |
| 509–545 | Activity Heatmap | GitHub-style grid rendered from 2D weeks array |
| 551–593 | Contact + Footer | Social links, CV download, copyright |
| 603–695 | `<script>` | `portfolio()` Alpine component: state, init/fetch, scroll observer, heatmap helpers |

### `data/portfolio.json` Schema

| Key | Type | Renders In |
|---|---|---|
| `meta` | `Object` | Navbar initials, hero name/tagline, CV path, footer |
| `social` | `Object` | LinkedIn, GitHub, Email, Google Scholar URLs |
| `experience[]` | `Array<{dates, role, company, description}>` | Experience timeline |
| `education[]` | `Array<{degree, institution, year, detail}>` | Education list |
| `projects[]` | `Array<{icon, title, impact, description, tools[], github}>` | Project cards |
| `publications[]` | `Array<{type, title, venue, year, link, tldr}>` | Publications & Talks |
| `methodology[]` | `Array<{step, icon, label, detail}>` | "How I Work" pipeline |
| `stack[]` | `Array<{category, skills[]}>` | Technical Stack |
| `reading` | `Object {title, author, publisher, progress}` | Currently Reading widget |
| `metrics[]` | `Array<{value, label}>` | Live metric counters |
| `githubActivity` | `Object {description, weeks[][]}` | Activity heatmap (2D array, values 0–5) |

---

## Common Content Updates

All of these are done by editing `data/portfolio.json` only.

### Add a new experience entry
Add an object to the `experience` array. **Newest first** — the array order is the display order.
```json
{
  "dates": "2026 — Present",
  "role": "Senior Data Scientist",
  "company": "Acme Corp",
  "description": "Led a team of 5 building recommendation systems."
}
```

### Add a new project card
Add an object to the `projects` array. The `icon` field takes any [Lucide icon name](https://lucide.dev/icons).
```json
{
  "icon": "brain",
  "title": "Project Name",
  "impact": "↑ 30% revenue",
  "description": "What it does and why it matters.",
  "tools": ["Python", "TensorFlow"],
  "github": "https://github.com/jjz17/project"
}
```

### Add a publication or talk
Add to `publications` array. Set `type` to `"paper"` (indigo accent) or `"talk"` (emerald accent).
```json
{
  "type": "paper",
  "title": "Paper Title",
  "venue": "Conference 2026",
  "year": "2026",
  "link": "https://arxiv.org/abs/...",
  "tldr": "One-sentence summary."
}
```

### Update the activity heatmap
Each sub-array in `githubActivity.weeks` is one week (7 values, Mon–Sun). Values range from `0` (no activity) to `5` (intense). Add/remove sub-arrays to change the width.

### Update metrics, reading, stack, education, methodology
Follow the same pattern — find the key in the JSON, add/edit/remove entries. The site re-renders automatically.

---

## Adding a New Section (Structural Change)

This requires changes to **both** `index.html` and `data/portfolio.json`.

### Step-by-step

1. **Add data to `portfolio.json`** — Create a new top-level key with your data:
   ```json
   "certifications": [
     { "name": "AWS ML Specialty", "year": "2025", "issuer": "Amazon" }
   ]
   ```

2. **Add the HTML section to `index.html`** — Insert a new `<section>` block in the main content area (between the existing sections, inside the `<template x-if="loaded">` wrapper). Follow the established patterns:
   ```html
   <section id="certifications" class="py-20 px-6 bg-neutral-50 dark:bg-neutral-900/50">
     <div class="max-w-3xl mx-auto fade-section">
       <h2 class="font-serif text-3xl font-bold mb-12">Certifications</h2>
       <div class="space-y-4">
         <template x-for="(cert, i) in d.certifications" :key="i">
           <div class="hover-lift rounded-xl p-5 bg-white dark:bg-neutral-800/60 border border-neutral-200 dark:border-neutral-700">
             <h3 class="font-serif text-lg font-semibold" x-text="cert.name"></h3>
             <p class="text-sm text-neutral-500 dark:text-neutral-400" x-text="cert.issuer + ' · ' + cert.year"></p>
           </div>
         </template>
       </div>
     </div>
   </section>
   ```

3. **Add navbar link** — Add an `<a>` tag in both the desktop nav and mobile nav dropdown:
   ```html
   <a href="#certifications" class="hover:text-accent transition-colors">Certs</a>
   ```

4. **Update the error fallback** — In the `portfolio()` function's `.catch()` block (~line 649), add the new key to the fallback object so the page doesn't break if JSON fails to load:
   ```js
   certifications: [],
   ```

5. **If using Lucide icons dynamically** — Icons set via `:data-lucide` in Alpine templates are already handled by the `lucide.createIcons()` call in `$nextTick`. No extra work needed.

---

## Design System & Conventions

### CSS Classes (reuse these)

| Class | Purpose |
|---|---|
| `fade-section` | Scroll-triggered fade-in (add to section's inner `<div>`) |
| `hover-lift` | Cards/buttons: translateY(-4px) + shadow on hover |
| `badge` | Small rounded pill for tags/labels |
| `glass-nav` | Frosted glass effect (navbar only) |
| `dot-grid` | The notebook dot background (body only) |
| `timeline-line` | Vertical accent gradient line (experience section) |
| `pipeline-connector` | Horizontal/vertical connector lines between methodology steps |
| `heatmap-cell` | Scale-on-hover for heatmap grid cells |
| `pub-line` | Left color bar on publication cards |
| `skeleton-pulse` | Loading animation |

### Color Tokens (Tailwind config)

| Token | Value | Usage |
|---|---|---|
| `surface-light` / `surface-dark` | `#fafaf9` / `#0f0f0f` | Page background |
| `ink-light` / `ink-dark` | `#1c1917` / `#e7e5e4` | Body text |
| `accent` | `#6366f1` (indigo) | Headings, links, active states, icon tints |
| `accent-hover` | `#818cf8` | Hover state for accent elements |

### Section Layout Pattern

Every section follows this structure:
```html
<section id="section-id" class="py-20 px-6 [optional: bg-neutral-50 dark:bg-neutral-900/50]">
  <div class="max-w-3xl mx-auto fade-section">  <!-- or max-w-4xl / max-w-5xl -->
    <h2 class="font-serif text-3xl font-bold mb-12">Section Title</h2>
    <!-- content -->
  </div>
</section>
```

- Alternate sections use the muted background (`bg-neutral-50 dark:bg-neutral-900/50`) for visual rhythm
- Section IDs must match navbar anchor hrefs
- `max-w-3xl` for text-heavy sections, `max-w-5xl` for card grids

### Typography

- **Headings:** `font-serif` (Playfair Display) — used on `<h1>`, `<h2>`, `<h3>`, and key data like metric values
- **Body text:** `font-sans` (Inter) — the default, no class needed
- **Accent text:** `text-accent` for links, labels, dates, highlighted terms
- **Muted text:** `text-neutral-500 dark:text-neutral-400` for secondary info
- **Small labels:** `text-xs tracking-widest uppercase text-accent` for category headers and date labels

### Dark Mode

- Managed via Alpine.js state (`darkMode`) toggling a `dark` class on `<html>`
- `darkMode` is initialized directly from the OS preference (`window.matchMedia('(prefers-color-scheme: dark)').matches`) in the state declaration — not in `init()` — to avoid a flash of the wrong theme
- The manual toggle button overrides the system default for the session
- Tailwind's `dark:` variant handles all color swaps
- Every background, text color, and border should have a `dark:` counterpart

### Responsive Breakpoints

- Mobile-first design
- `sm:` (640px) — switch from stacked to side-by-side layouts
- `lg:` (1024px) — 3-column project card grid
- Navbar collapses to hamburger menu below `sm:` — the icon toggles between `menu` (hamburger) and `x` (close) using `x-show` on both Lucide icons

---

## Alpine.js Component Reference

The `portfolio()` function (bottom of `index.html`) exposes:

| Property | Type | Purpose |
|---|---|---|
| `darkMode` | `boolean` | Dark mode toggle state |
| `mobileNav` | `boolean` | Mobile nav drawer open/closed |
| `loaded` | `boolean` | `true` after JSON fetch completes |
| `activeStep` | `number\|null` | Which methodology step is expanded |
| `d` | `object` | The portfolio data object (entire JSON) |

| Method | Purpose |
|---|---|
| `init()` | Auto-called by Alpine. Detects OS dark mode, fetches JSON, calls `lucide.createIcons()` and `initScrollObserver()` after render |
| `initScrollObserver()` | Sets up `IntersectionObserver` on `.fade-section` elements |
| `heatmapColor(level)` | Returns Tailwind classes for heatmap cell (levels 0–5) |
| `heatmapLabel(level)` | Returns tooltip string for heatmap cell |

### Adding new interactive behavior

1. Add a state variable to the `return` object in `portfolio()`
2. Add a helper method if needed
3. Reference it in HTML via Alpine directives (`x-data`, `x-show`, `@click`, etc.)
4. If the new feature dynamically inserts Lucide icons, call `this.$nextTick(() => lucide.createIcons())` after the relevant state change

---

## Testing Locally

The site uses `fetch()` for JSON, so you **must** serve it over HTTP (not `file://`).

```bash
# Python
python -m http.server 8000

# Node
npx serve .

# VS Code: Right-click index.html → Open with Live Server
```

### What to verify after changes

- [ ] Site loads without console errors
- [ ] New/edited content appears correctly
- [ ] Dark mode toggle works (check both modes)
- [ ] Mobile layout: hamburger menu, stacked cards, no horizontal overflow
- [ ] Scroll animations fire on new sections (needs `fade-section` class)
- [ ] All Lucide icons render (no empty spaces where icons should be)
- [ ] Links open correctly (social, project GitHub, publications)

---

## Gotchas & Pitfalls

1. **JSON syntax errors kill the entire site.** If the page shows only the loading spinner forever, check `data/portfolio.json` for trailing commas, missing quotes, etc. Open the browser console for the fetch error.

2. **Lucide icons must use valid icon names.** Browse [lucide.dev/icons](https://lucide.dev/icons) to find names. If an icon doesn't render, the name is wrong.

3. **Alpine.js `defer` is required.** The Alpine `<script>` tag must have `defer` so the DOM is ready before Alpine initializes. Don't remove it.

4. **New sections must be inside `<template x-if="loaded">`** (the main content wrapper). Anything outside it won't have access to `d`.

5. **Alternate section backgrounds.** Sections alternate between no-background and `bg-neutral-50 dark:bg-neutral-900/50`. Keep this rhythm when inserting new sections.

6. **The error fallback object must stay in sync.** If you add a new top-level key to `portfolio.json`, also add it to the `.catch()` fallback in `portfolio()` so the page degrades gracefully.

7. **Tailwind CDN is for development/prototyping.** For production performance, consider migrating to the Tailwind CLI or PostCSS build. This is optional — the CDN works fine for a portfolio site.

8. **`x-html` vs `x-text`.** Use `x-text` by default (safe, escapes HTML). Only use `x-html` when you intentionally need rendered HTML (currently used for `edu.detail`). Be aware of XSS implications if the JSON source is untrusted.

---

## Claude Code Instructions

When assisting with this project:

- **Content changes** = edit `data/portfolio.json` only. Never touch `index.html` for content.
- **New sections** require changes in both files. Follow the step-by-step in "Adding a New Section" above.
- **Always validate JSON** after editing `portfolio.json` — a single syntax error breaks the whole site.
- **Preserve the design system.** Reuse existing CSS classes (`hover-lift`, `fade-section`, `badge`, etc.) and Tailwind tokens (`accent`, `surface-*`, `ink-*`) rather than introducing new styles.
- **Dark mode is mandatory.** Every new element needs both light and `dark:` variants.
- **Keep the zero-build philosophy.** Do not introduce npm, webpack, Vite, or any build tooling. Everything runs from CDN + static files.
- **Icon references** use Lucide icon names as strings (e.g., `"brain"`, `"rocket"`). Use `:data-lucide="variable"` for dynamic icons in Alpine templates.
- **Test by serving over HTTP.** Remind the user that `file://` won't work due to `fetch()`.
- **Section background alternation.** Check whether a new section should have the muted background to maintain visual rhythm.
- **Update the fallback.** When adding new JSON keys, update the `.catch()` fallback object in `portfolio()`.
