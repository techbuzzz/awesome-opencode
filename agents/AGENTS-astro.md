# Project: [SiteName] — Astro + Tailwind CSS

## Overview
[Brief description of the site/app]

## Tech Stack
- **Framework:** Astro 5 (SSG + optional SSR)
- **Styling:** Tailwind CSS v4
- **Language:** TypeScript (strict mode)
- **Testing:** Vitest + Playwright (E2E)
- **Content:** Astro Content Collections (MDX)
- **Components:** Astro native + React islands where needed
- **Deployment:** Vercel / Netlify / Cloudflare Pages

## Project Structure
```
src/
├── components/          # Reusable UI components (.astro, .tsx)
│   ├── ui/              # Base components (Button, Card, Input...)
│   └── layout/          # Layout components (Header, Footer, Nav)
├── layouts/             # Page layouts (Base.astro, Blog.astro)
├── pages/               # File-based routing
│   └── blog/
│       └── [...slug].astro
├── content/             # Content collections
│   ├── config.ts        # Collection schemas
│   └── blog/            # Markdown/MDX posts
├── lib/                 # Utilities, helpers, API clients
└── styles/              # Global styles (globals.css)
public/                  # Static assets
astro.config.mjs
tailwind.config.mjs      # (v3) or managed via CSS @theme (v4)
tsconfig.json
```

## Code Standards

### TypeScript
- Strict mode enabled — no `any`, no `@ts-ignore` without explanation
- All component Props defined with `interface Props {}`
- Use `type` for unions/primitives, `interface` for object shapes

### Astro Components
- Keep frontmatter (---) focused on data fetching and prop types
- Extract repeated logic to `src/lib/` utilities
- Use `<Image />` from `astro:assets` for all images (never `<img>`)
- Use `<Picture />` for art-directed images

### Content Collections
- All collections have Zod schema in `src/content/config.ts`
- Never access frontmatter without validation
- Use `getCollection()` with filter for drafts

### Tailwind
- Mobile-first: base styles for mobile, add `sm:`, `md:`, `lg:` as needed
- Prefer design tokens (CSS variables) over magic numbers
- Use `cn()` helper for conditional class names
- Dark mode via `dark:` prefix (class-based strategy)

### Performance
- `client:visible` for below-fold interactive components
- `client:idle` for low-priority interactivity
- `client:load` only for critical above-fold interactivity
- Static components use no `client:*` directive

## Common Commands
```bash
# Dev server
npm run dev

# Build
npm run build

# Preview build
npm run preview

# Type check
npx astro check

# Run tests
npx vitest

# E2E tests
npx playwright test
```

## SEO Checklist (all pages)
- [ ] `<title>` tag set
- [ ] `<meta name="description">` set (50-160 chars)
- [ ] OG tags (og:title, og:description, og:image)
- [ ] Canonical URL set
- [ ] Sitemap generated (via @astrojs/sitemap)
- [ ] Structured data (JSON-LD) for key content types

## Do NOT
- Put `<img>` tags directly — use `<Image />` from astro:assets
- Use `client:load` for non-critical components
- Write inline `<style>` when Tailwind utility covers the case
- Commit `.env.local` (only `.env.example`)
- Use `document` or `window` in Astro frontmatter (SSR context)
