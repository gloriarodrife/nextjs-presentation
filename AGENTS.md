# AI Agent Guide (AGENTS.md) - Next.js Presentation

This document provides context, design conventions, and technical guidelines for AI agents and developers to collaborate effectively, consistently, and safely in this repository.

---

## 1. Project Overview

- **Project Name:** `nextjs-presentation`
- **Context:** Individual project for the *Web Programming* course (WCC).
- **Author:** Gloria Rodriguez Fernandez.
- **Purpose:** An interactive, developer-oriented slide deck introducing **Next.js**, contrasting it against Vanilla JavaScript, and explaining why it is a compelling modern web development solution (file-system routing, server-side rendering, integrated API routes, performance/SEO, approachable learning curve, and open-source accessibility).
- **Primary Tool:** [Slidev](https://sli.dev/) (`@slidev/cli` v53+), a developer-focused presentation engine built on top of Vue 3, Vite, Markdown, and UnoCSS/Tailwind.

---

## 2. Tech Stack

| Component | Technology / Version | Description |
| :--- | :--- | :--- |
| **Slide Deck Engine** | `@slidev/cli` (^53.0.0) | Markdown-to-HTML presentation compiler |
| **Slidev Themes** | `@slidev/theme-default`, `@slidev/theme-seriph` | Base presentation themes |
| **UI Library** | `vue` (^3.5.33) | Custom Vue component integration |
| **Styling & Utilities** | Slidev-integrated UnoCSS / Tailwind + Custom CSS | Utility classes and custom presentation theme styles |
| **Hosting & Deployment** | Vercel (`vercel.json`) and Netlify (`netlify.toml`) | Static SPA output generated in `dist/` |

---

## 3. Repository Structure

```text
NextJS-presentation/
├── slides.md               # Main presentation content, slide definitions, and metadata
├── styless.css             # Custom stylesheet (see Technical Notice below)
├── package.json            # Node.js dependencies and script definitions
├── package-lock.json       # Locked dependency tree
├── pnpm-workspace.yaml     # Workspace configuration for pnpm environments
├── components/             # Reusable custom Vue components (auto-imported by Slidev)
├── layouts/                # Custom Slidev slide templates and layouts
├── snippets/               # External code snippets imported directly into slides
│   └── external.ts         # Sample snippet with #region tags
├── public/                 # Static assets (images, stickers, icons)
│   └── sticker.png         # Sticker graphic used in the Q&A slide
├── netlify.toml            # Netlify build and SPA rewrite routing configuration
├── vercel.json             # Vercel build and SPA rewrite configuration
├── README.md               # Quickstart guide
└── AGENTS.md               # This AI agent guide and system reference
```

---

## 4. Key Commands and Workflows

Standard scripts configured in `package.json`:

```bash
# Start local development server (defaults to http://localhost:3030)
npm run dev

# Compile presentation into a static Single Page Application (SPA) in dist/
npm run build

# Export slides to PDF or PPTX (requires Playwright when run locally)
npm run export
```

---

## 5. Slide Architecture (`slides.md`)

Slidev compiles a single Markdown file (`slides.md`) into slides delimited by `---`:

1. **Headmatter (Global Frontmatter):**
   - Configures presentation defaults (`theme: default`).
   - Supports global attributes such as `title`, `info`, `highlighter`, `lineNumbers`, `css`, etc.
2. **Slide Delimiters and Properties:**
   - Every slide begins after a `---` separator.
   - Slide-specific frontmatter attributes include:
     - `layout: center` | `layout: two-cols` | `layout: two-cols-header` | `layout: default`
     - `class: text-center` | `class: flex flex-col justify-center pt-8`
     - `zoom: 0.8` (scales slide content down to prevent overflow when displaying longer code blocks)
3. **Current Presentation Outline:**
   1. **Slide 1:** Title / Cover (Next.js overview).
   2. **Slide 2:** What is a Framework vs. Vanilla JavaScript? (Concept cards).
   3. **Slide 3:** Vanilla JS: creating an "About" page (HTML + Client Script + Express server setup).
   4. **Slide 4:** Next.js: creating an "About" page (`create-next-app` + `page.tsx`).
   5. **Slide 5:** Feature Comparison Table (Vanilla JS vs. Next.js).
   6. **Slide 6:** Why Next.js? (4 core pillars).
   7. **Slide 7:** Friendly learning curve (example using `<Link href="...">`).
   8. **Slide 8:** Optimized for speed and SEO (SSR vs. Client-side empty DOM delivery).
   9. **Slide 9:** File-system routing (Directory mapping inside `app/`).
   10. **Slide 10:** Unified frontend and backend (`app/api/.../route.ts`).
   11. **Slide 11:** Server-side execution (Secure data fetching with `fetch()`).
   12. **Slide 12:** Transition slide ("And one last reason...").
   13. **Slide 13:** Free & Open Source ("Student budget approved").
   14. **Slide 14:** Thematic programming GIF.
   15. **Slide 15:** Q&A slide (`/sticker.png`).
   16. **Slide 16:** Closing and attribution ("Gloria Rodriguez Fernandez").

---

## 6. Design System and Visual Conventions

### Color Palette
Defined in `styless.css` and reinforced with UnoCSS / Tailwind utility classes:
- Primary Dark Green (`--primary-green`): `#1b4332`
- Accent Green (`--accent-green`): `#2d6a4f`
- Tailwind Emerald Shades: `bg-emerald-600`, `text-emerald-800`
- Ambient Background: `linear-gradient(135deg, #f4f9f4 0%, #e8f5e9 100%)`
- Glassmorphism Cards: Translucent white surfaces (`rgba(255, 255, 255, 0.85)`), subtle borders, soft shadow.

### Custom Reusable CSS Classes
- `.card`: Styled content containers featuring rounded corners, elevated shadow, and balanced padding.
- `.bolt`: Renders lightning bolt (`⚡`) bullet icons for unordered list items (`<li>`).
- Section divider: `<div class="w-16 h-1 bg-emerald-600 my-4"></div>`.

---

## 7. Guidelines for AI Agents Modifying Code

1. **Maintain Tone and Voice:**
   - The presentation is written in English.
   - Maintain an engaging, friendly, educational tone tailored for students and web developers.
   - Preserve direct comparisons and clear side-by-side contrast (e.g., Vanilla JS vs. Next.js).

2. **Managing Slide Content in `slides.md`:**
   - When introducing slides with dense code snippets or long text, add `zoom: 0.8` or `zoom: 0.85` in the slide frontmatter to avoid vertical overflow.
   - For two-column layouts (`two-cols` or `two-cols-header`), maintain proper slot separators: `::left::` and `::right::`.
   - Use Slidev syntax highlighting features like line highlighting `{1-3|5|all}` when walking through code sequentially.

3. **Assets and Components:**
   - Store public static assets in `public/` and reference them starting with `/` (e.g., `/sticker.png`, never `public/sticker.png`).
   - Create custom interactive Vue components in `components/ComponentName.vue` (Slidev automatically resolves and imports them).

4. **Production Deployments:**
   - Preserve SPA rewrite rules in `vercel.json` and `netlify.toml` targeting `dist/index.html`. Slidev builds a Single Page Application that requires client-side route fallback in production.

---

## 8. Technical Observations & Recommendations

> [!WARNING]
> **CSS File Naming:** The stylesheet is named `styless.css` (with two 's' characters).
> Slidev automatically discovers and loads files named `style.css` or `styles.css` from the root.
> If retaining `styless.css`, declare it explicitly in the head frontmatter of `slides.md`:
> ```yaml
> ---
> theme: default
> css: ./styless.css
> ---
> ```
> Alternatively, rename the file to `style.css` so Slidev injects it automatically without extra configuration.
