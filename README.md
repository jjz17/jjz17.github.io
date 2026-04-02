# 📊 Jason Zhang — Data Scientist Portfolio

> A minimalist, high-end single-page portfolio powered by a **JSON data layer**.  
> **Zero build steps.** Just HTML + CDN. Edit one JSON file to update everything.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![Alpine.js](https://img.shields.io/badge/Alpine.js-8BC0D0?style=flat&logo=alpinedotjs&logoColor=black)
![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-222?style=flat&logo=githubpages&logoColor=white)

---

## 🖼️ Preview

| Light Mode | Dark Mode |
|---|---|
| ![Light mode screenshot](https://via.placeholder.com/600x400?text=Light+Mode) | ![Dark mode screenshot](https://via.placeholder.com/600x400?text=Dark+Mode) |

> **Tip:** Replace the placeholder images above with actual screenshots after deployment.

---

## ✨ Key Features

| Feature | Why it matters |
|---|---|
| **JSON-driven content** | All dynamic content lives in `data/portfolio.json`. Update one file — the site re-renders automatically. No HTML editing required. |
| **Publications & Talks** | Peer-reviewed papers and conference talks with TL;DR summaries. Color-coded by type (paper vs. talk). Essential for demonstrating thought leadership. |
| **"How I Work" Pipeline** | An interactive, clickable methodology diagram (Frame → Explore → Model → Deploy → Monitor). Shows DS maturity and process thinking to hiring managers. |
| **Activity Heatmap** | A GitHub-style contribution grid rendered from JSON data. Visual proof of consistency — speaks volumes to both technical peers and leadership. |
| **Dark Mode** | OS-aware + manual toggle. Powered by Alpine.js + Tailwind's `dark:` variant. |
| **Dot-grid notebook aesthetic** | Pure CSS, zero image assets. Evokes the analytical identity of a data scientist. |
| **Glassmorphism navbar** | Frosted-glass sticky header that stays present without competing with content. |
| **Mobile-first responsive** | Fully responsive with a hamburger menu for mobile navigation. |

---

## 🎨 Design Decisions

### Why a dot-grid background?
Data scientists live in notebooks — Jupyter notebooks, graph paper, whiteboards. The subtle CSS dot-grid pattern nods to that analytical identity without overwhelming the content. It's generated with pure CSS (`radial-gradient`), so there are **zero extra image assets**.

### Why Playfair Display + Inter?
- **Playfair Display** (Serif, headings) evokes editorial credibility — the kind you see in *The Economist* or *The New York Times*. For a data scientist, it signals that you take communication as seriously as computation.
- **Inter** (Sans-serif, body) is one of the most legible screen fonts available, designed specifically for UI. The pairing creates a sophisticated contrast between narrative headings and clean, scannable body text.

### Why Tailwind CSS via CDN?
- **No build step.** The entire site works from a single `index.html` + one JSON file.
- **Utility-first classes** make it trivial to adjust spacing, colours, and responsive behaviour.
- **Dark mode** is handled natively via Tailwind's `dark:` variant.

### Why Alpine.js?
Alpine.js provides reactive, declarative behaviour (dark-mode toggle, data fetching, template rendering) in under 15 KB. It loads from a CDN — one `<script>` tag. It's the engine that reads `portfolio.json` and renders all sections dynamically.

### Why a JSON data layer?
Separating content from presentation means:
- **Non-technical collaborators** can update your portfolio by editing a JSON file.
- **Adding new entries** (projects, publications, jobs) never requires touching HTML.
- **Version control** diffs are clean — you see exactly what content changed.
- **Future-proof** — the same JSON can feed a future React/Svelte rebuild.

---

## 🗂️ Project Structure

```
.
├── index.html              # Single-page portfolio (reads from JSON)
├── data/
│   └── portfolio.json      # ★ ALL editable content lives here
├── README.md               # You are here
└── assets/                 # (Optional) CV PDF, images, etc.
    └── Jason_Zhang_CV.pdf
```

---

## 📝 Architecture: How the JSON Data Layer Works

```
┌─────────────────────┐       fetch()         ┌──────────────────────┐
│                     │  ──────────────────>  │                      │
│    index.html       │                       │  data/portfolio.json │
│  (Alpine.js app)    │  <──────────────────  │  (all content)       │
│                     │       JSON data       │                      │
└─────────────────────┘                       └──────────────────────┘
         │
         ▼
   Alpine.js renders
   all sections via
   x-for / x-text / x-html
```

On page load:
1. Alpine.js `init()` fires a `fetch('data/portfolio.json')` request.
2. The JSON response populates the reactive `d` object.
3. All `<template x-for>` loops and `x-text` bindings render the content.
4. Lucide icons are re-initialized after render via `$nextTick`.

---

## 🧩 The JSON Schema

Here's a quick reference for every section in `data/portfolio.json`:

| Key | Type | Drives Section |
|---|---|---|
| `meta` | Object | Navbar initials, hero name/tagline, CV path, footer text |
| `social` | Object | LinkedIn, GitHub, Email, Google Scholar URLs |
| `experience[]` | Array of Objects | Experience Timeline |
| `education[]` | Array of Objects | Education list |
| `projects[]` | Array of Objects | Project cards (icon, title, impact, tools, GitHub link) |
| `publications[]` | Array of Objects | Papers & Talks section (type, title, venue, TL;DR, link) |
| `methodology[]` | Array of Objects | "How I Work" interactive pipeline |
| `stack[]` | Array of Objects | Technical Stack categories & skills |
| `reading` | Object | Currently Reading book widget |
| `metrics[]` | Array of Objects | Live metric counters |
| `githubActivity` | Object | Activity heatmap (description + 2D array of weeks) |

---

## 🚀 Local Testing

### Option A: VS Code Live Server (Recommended)

1. Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension in VS Code.
2. Open the project folder in VS Code.
3. Right-click `index.html` → **Open with Live Server**.
4. Your browser will open `http://127.0.0.1:5500/index.html` with hot-reload.

> ⚠️ **Important:** You must use a local server (not `file://`) because the site uses `fetch()` to load JSON, which requires HTTP.

### Option B: Python HTTP Server

```bash
# Navigate to the project folder
cd path/to/your-portfolio

# Python 3
python -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

### Option C: Node.js (npx)

```bash
npx serve .
```

Then open the URL printed in the terminal (usually `http://localhost:3000`).

---

## 🌐 Deploying to GitHub Pages

### Step-by-step

1. **Create a GitHub repository**
   - Go to [github.com/new](https://github.com/new).
   - Name it `your-username.github.io` for a user site, or any name for a project site.
   - Set it to **Public**.

2. **Push your code**
   ```bash
   git init
   git add .
   git commit -m "Initial commit — portfolio site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Go to your repo → **Settings** → **Pages** (left sidebar).
   - Under **Source**, select **Deploy from a branch**.
   - Choose **`main`** branch and **`/ (root)`** folder.
   - Click **Save**.

4. **Wait ~60 seconds**, then visit:
   - User site: `https://your-username.github.io`
   - Project site: `https://your-username.github.io/repo-name`

### Custom Domain (Optional)

1. In **Settings → Pages**, enter your custom domain (e.g., `janedoe.com`).
2. Add a `CNAME` file to the repo root containing just your domain.
3. Configure your DNS provider with the [GitHub Pages IP addresses](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

---

## 🛠️ Maintenance Guide

> **The golden rule:** To update content, you only ever edit `data/portfolio.json`.  
> You never need to touch `index.html` unless you're changing layout or adding new sections.

### 👤 Updating Personal Info

Edit the `meta` and `social` objects at the top of `portfolio.json`:

```jsonc
"meta": {
  "name": "Your Name",
  "initials": "YN",
  "title": "Your Title",
  // ...
},
"social": {
  "linkedin": "https://linkedin.com/in/yourprofile",
  "github": "https://github.com/yourusername",
  "email": "you@email.com",
  "scholar": "https://scholar.google.com/citations?user=YOURID"
}
```

### 📅 Adding a New Experience Entry

Add a new object to the `experience` array (newest first):

```jsonc
{
  "dates": "2026 — Present",
  "role": "Lead Data Scientist",
  "company": "NewCo",
  "description": "Describe your impact here."
}
```

### 🎓 Adding a New Education Entry

Add a new object to the `education` array:

```jsonc
{
  "degree": "Ph.D. Machine Learning",
  "institution": "MIT",
  "year": "2028",
  "detail": "Dissertation on causal inference in recommender systems."
}
```

### 📦 Adding a New Project Card

Add a new object to the `projects` array:

```jsonc
{
  "icon": "brain",          // Any Lucide icon name: https://lucide.dev/icons
  "title": "Project Name",
  "impact": "↑ 30% revenue",
  "description": "What it does and why it matters.",
  "tools": ["Python", "TensorFlow", "Airflow"],
  "github": "https://github.com/you/project"
}
```

### 📄 Adding a New Publication or Talk

Add to the `publications` array:

```jsonc
{
  "type": "paper",           // "paper" or "talk"
  "title": "Your Paper Title",
  "venue": "Conference Name 2026",
  "year": "2026",
  "link": "https://arxiv.org/abs/...",
  "tldr": "One-sentence summary of the contribution."
}
```

### 🔬 Editing the "How I Work" Pipeline

Update or add steps in the `methodology` array:

```jsonc
{
  "step": "Validate",        // Short label shown on the icon
  "icon": "check-circle",    // Lucide icon name
  "label": "A/B Validation", // Full label shown below
  "detail": "Explain what this step involves."
}
```

### 🧰 Adding / Removing Skills

Edit the `stack` array. Each entry has a `category` and a `skills` array:

```jsonc
{
  "category": "GenAI & LLMs",
  "skills": ["LangChain", "LlamaIndex", "OpenAI", "Anthropic", "vLLM"]
}
```

### 📖 Updating "Currently Reading"

```jsonc
"reading": {
  "title": "New Book Title",
  "author": "Author Name",
  "publisher": "Publisher, 2026",
  "progress": 40
}
```

### 📊 Updating Live Metrics

```jsonc
"metrics": [
  { "value": "12", "label": "Models in Production" },
  { "value": "5.1M", "label": "Daily Predictions" }
]
```

### 🟩 Updating the Activity Heatmap

The `githubActivity.weeks` is a 2D array where each sub-array is a week (7 days, Mon–Sun) and each value is an intensity level from `0` (no activity) to `5` (intense). Add or remove weeks to change the width:

```jsonc
"githubActivity": {
  "description": "Contributions in the last 20 weeks",
  "weeks": [
    [0,2,3,1,4,2,0],
    [1,3,4,2,5,3,1],
    // ... add more weeks
  ]
}
```

---

## 📝 Tech Stack Summary

| Layer | Technology | Purpose |
|---|---|---|
| Structure | HTML5 | Semantic single-page layout |
| Styling | Tailwind CSS (CDN) | Utility-first, responsive, dark mode |
| Interactivity | Alpine.js (CDN) | Data fetching, rendering, dark-mode toggle |
| Data | JSON (`data/portfolio.json`) | Single source of truth for all content |
| Icons | Lucide Icons (CDN) | Lightweight, customizable SVG icons |
| Hosting | GitHub Pages | Free, fast, global CDN |

---

## 📄 License

This project is open source under the [MIT License](https://opensource.org/licenses/MIT).  
Feel free to fork, customise, and make it your own.

---

<p align="center">
  <em>Built with ☕ and curiosity.</em>
</p>
