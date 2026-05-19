# IREKAI Website

## Quick preview

Open `irekai-preview.html` directly in any modern browser — no build step required.
It loads Vue 3 + Vue Router from CDN and contains the complete website with all pages.

---

## Vue source project (for production deployment)

The `src/` folder contains the full Vue 3 + Vite source project.

### Structure

```
irekai-website/
  index.html              ← Vite entry point
  vite.config.js
  package.json
  public/
    favicon.svg
  src/
    main.js               ← App bootstrap + router
    App.vue               ← Root layout (NavBar + RouterView + Footer)
    assets/
      style.css           ← Design system (CSS variables, global classes)
    components/
      NavBar.vue          ← Sticky navbar with mobile menu + product dropdown
      SiteFooter.vue      ← Footer with nav links
    views/
      HomeView.vue        ← Landing page (IREKAI animation + product grid)
      AboutView.vue       ← About IREKAI
      QuantumReadinessView.vue   ← Flagship product page
      MaturityModelView.vue      ← PQC Maturity Model page
      SupplierManagementView.vue ← Supplier Management Programme page
      CodeScanningView.vue       ← Cryptographic Code Scanner page
```

### Build for production

```bash
cd irekai-website
npm install
npm run build        # outputs to dist/
npm run preview      # preview the built site locally
```

### Dev server

```bash
npm run dev          # starts at http://localhost:5173
```

---

## Adding assets later

- **Quantum Readiness Assessment document** → add to `public/assets/` and link from `QuantumReadinessView.vue`
- **Code Scanner animation** → replace the terminal card in `CodeScanningView.vue` with your HTML animation
- **Supplier Management teaser PDF** → link from `SupplierManagementView.vue`

## Design system

| Token | Value |
|-------|-------|
| Background | `#0c0a09` (stone-950) |
| Primary accent | `#2dd4bf` (teal) |
| Maturity Model | `#fbbf24` (amber) |
| Supplier Mgmt | `#a78bfa` (violet) |
| Code Scanner | `#e879f9` (fuchsia) |
| Display font | Fraunces (Google Fonts) |
| Mono font | JetBrains Mono (Google Fonts) |

---

## Deployment (GitHub Pages, local build)

This project is configured for local deploys to GitHub Pages (no GitHub Actions).

### One-time GitHub setup

1. Push this repository to GitHub.
2. In GitHub, open **Settings > Pages**.
3. Under **Build and deployment**:
  - Source: **Deploy from a branch**
  - Branch: **gh-pages**
  - Folder: **/ (root)**
4. Save.

### Local deploy flow

```bash
cd irekai-website
npm install
npm run deploy
```

What `npm run deploy` does:

- Runs `npm run build` first (`predeploy` hook)
- Publishes `dist/` to the `gh-pages` branch

### Notes

- The router uses hash history (`/#/about`), so deep-link refreshes work on GitHub Pages.
- `base` is configured as `./` in Vite, so built assets stay relative and work from a project pages path.
- If your default branch is protected, this workflow still works because deployment pushes to `gh-pages`, not to your default branch.
- Custom domain is controlled by `public/CNAME` (currently `irekai.nl`). Keep exactly one domain per file.
