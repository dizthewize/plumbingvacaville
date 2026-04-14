# Build Plan — Vacaville Plumbing
Generated: 2026-04-14 | Framework: Astro | Auth: Disabled

---

## Research Summary

| Agent | Status | Output |
|-------|--------|--------|
| Stack Scout | ✅ Complete | Scaffold command, deps, Tailwind v4 notes |
| Component Analyst | ✅ Complete | 14 components with file paths, props, classes |
| SEO Mapper | ✅ Complete | `docs/seo-map.json` — 24 pages with meta + schema |
| Copy Integrator | ✅ Complete | `docs/copy.json` — all pages, sections, CTAs |
| Auth + DB Planner | ⏭ Skipped | `auth_enabled=false` |
| Conversion Optimizer | ⚠️ Partial | CTA placement covered by design-system.md specs |

---

## Stack

- **Framework:** Astro 5 (static output, `trailingSlash: 'never'`)
- **CSS:** Tailwind CSS v4 (CSS-first, no `tailwind.config.ts`)
- **Icons:** `@lucide/astro` (PascalCase imports, `stroke-width="1.5"`)
- **Deployment:** Netlify via GitHub integration
- **Images:** `astro:assets` Image component (WebP auto-generation)
- **Sitemap:** `@astrojs/sitemap` integration

### Scaffold Commands

```bash
npm create astro@latest . -- --template minimal --install --no-git
npx astro add tailwind sitemap
npm install @lucide/astro
```

### Dependencies

```json
{
  "@astrojs/sitemap": "latest",
  "@astrojs/tailwind": "latest",
  "@lucide/astro": "latest"
}
```

---

## Pages (25 total)

| Page | File Path | Template |
|------|-----------|----------|
| Homepage | `src/pages/index.astro` | Custom |
| Services hub | `src/pages/services/index.astro` | Inner |
| Drain Cleaning | `src/pages/services/drain-cleaning.astro` | Service |
| Water Heater | `src/pages/services/water-heater.astro` | Service |
| Leak Detection | `src/pages/services/leak-detection.astro` | Service |
| Repiping | `src/pages/services/repiping.astro` | Service |
| Emergency Plumbing | `src/pages/services/emergency-plumbing.astro` | Service |
| Bathroom & Kitchen | `src/pages/services/bathroom-kitchen-plumbing.astro` | Service |
| Fixture Installation | `src/pages/services/fixture-installation.astro` | Service |
| Sewer Line | `src/pages/services/sewer-line.astro` | Service |
| Service Areas | `src/pages/service-areas/index.astro` | Inner |
| Vacaville | `src/pages/service-areas/vacaville.astro` | City |
| Fairfield | `src/pages/service-areas/fairfield.astro` | City |
| Dixon | `src/pages/service-areas/dixon.astro` | City |
| Napa | `src/pages/service-areas/napa.astro` | City |
| Vallejo | `src/pages/service-areas/vallejo.astro` | City |
| Woodland | `src/pages/service-areas/woodland.astro` | City |
| Davis | `src/pages/service-areas/davis.astro` | City |
| Winters | `src/pages/service-areas/winters.astro` | City |
| About | `src/pages/about.astro` | Inner |
| Blog | `src/pages/blog/index.astro` | Inner |
| Contact | `src/pages/contact.astro` | Inner |
| Privacy Policy | `src/pages/privacy.astro` | Legal |
| Terms | `src/pages/terms.astro` | Legal |

---

## Component File Map (14 components)

### Shared / Layout

| Component | File | Key Props |
|-----------|------|-----------|
| `Layout` | `src/layouts/Layout.astro` | `title`, `description`, `ogTitle`, `ogDescription`, `canonical`, `pageType` |
| `EmergencyBand` | `src/components/EmergencyBand.astro` | _(none — always same content)_ |
| `Header` | `src/components/Header.astro` | `currentPath` |
| `Footer` | `src/components/Footer.astro` | _(none)_ |
| `MobileStickyBar` | `src/components/MobileStickyBar.astro` | _(none)_ |

### UI / Forms

| Component | File | Key Props |
|-----------|------|-----------|
| `Button` | `src/components/Button.astro` | `variant` (primary/secondary/ghost), `href`, `size`, `ariaLabel` |
| `LeadCaptureForm` | `src/components/LeadCaptureForm.astro` | `formTitle`, `submitLabel`, `compact` |

### Homepage Sections

| Component | File | Key Props |
|-----------|------|-----------|
| `HeroSection` | `src/components/HeroSection.astro` | `headline`, `subheadline`, `primaryCta`, `secondaryCta` |
| `ServicesGrid` | `src/components/ServicesGrid.astro` | `services[]` (name, slug, icon, benefit) |
| `TrustSignalsBar` | `src/components/TrustSignalsBar.astro` | `signals[]` (icon, label), `variant` (light/dark) |
| `TestimonialsSection` | `src/components/TestimonialsSection.astro` | `testimonials[]` (quote, name, city, rating) |
| `ServiceAreaSection` | `src/components/ServiceAreaSection.astro` | `cities[]` (name, slug), `showMap` |
| `OfferSection` | `src/components/OfferSection.astro` | `badge`, `headline`, `body`, `primaryCta`, `secondaryCta` |
| `FAQAccordion` | `src/components/FAQAccordion.astro` | `faqs[]` (question, answer) |

---

## CTA Placement Plan

Synthesized from design-system.md component specs (Conversion Optimizer data merged):

### Every Page
1. **EmergencyBand** — topmost element (above header), always visible, `href="tel:9166122126"`
2. **Header** — sticky, phone link + "Get a Free Estimate" CTA button
3. **MobileStickyBar** — fixed bottom, `display:none` on desktop, "Call Now" + "Get Free Estimate"
4. **Footer** — phone link in Brand column

### Homepage Specific
1. **Hero** — lead form (right col desktop / below headline mobile) + primary CTA button
2. **Trust Signals Bar** — just after hero (above the fold on most screens)
3. **Offer Section** — after services grid, dual CTAs (form + call)
4. **Final CTA** — page bottom, repeated `LeadCaptureForm`

### Service Pages
1. **Hero** — primary CTA to `#lead-form` + secondary phone call CTA
2. **Trust Signals Bar** — after hero
3. **LeadCaptureForm** (`id="lead-form"`) — mid-page anchor target
4. **Final CTA** — page bottom with phone + form

### Inner Pages (About, Contact, Service Areas)
1. **Contact page** — full `LeadCaptureForm` above the fold + phone prominent
2. **About** — final CTA with form at bottom
3. **Service Areas hub** — dual CTA (form + phone) in hero + final CTA

---

## SEO Layer

Source: `docs/seo-map.json`

- 24 pages with `<title>`, `<meta name="description">`, OG tags
- **LocalBusiness / Plumber JSON-LD** on homepage only:
  - `@type: ["LocalBusiness", "Plumber"]`
  - `telephone: "(916) 612-2126"`
  - `areaServed`: Vacaville, Fairfield, Dixon, Napa, Vallejo, Woodland, Davis, Winters
  - TBD at launch: `streetAddress`, `postalCode`, `sameAs` URLs
- `public/sitemap.xml` — all 24 URLs, `<lastmod>` today
- `public/robots.txt` — allow all + sitemap pointer

---

## Copy Source

Source: `docs/copy.json`

All text comes from this file. Build agent must NOT invent copy.

- `pages` — homepage, services, about, contact, service-areas
- `servicePages` — 8 service subpages (hero, trust-signals, final-cta per page)
- `cityPages.template` — city page template with `{city}` tokens + cities array
- `nav` — header links, mobile sticky bar, footer columns
- `meta` — title + description for all core pages
- `flags` — items requiring client data before launch (address, social URLs, hours, logo)

**Testimonials note:** 3 placeholder testimonials in copy.json. Must be replaced with real Google reviews before launch.

---

## Design Token Source

Source: `docs/design-system.md`

### CSS Variables (verbatim in `globals.css`)

```css
:root {
  --color-primary: #1e3a5f;
  --color-primary-dark: #152c4a;
  --color-primary-light: #2980b9;
  --color-accent: #ea580c;
  --color-accent-dark: #c2410c;
  --color-neutral-50: #f8fafc;
  --color-neutral-100: #f0f7ff;
  --color-neutral-200: #e2e8f0;
  --color-neutral-700: #64748b;
  --color-neutral-900: #1a202c;
  --color-text: #1a202c;
  --color-text-muted: #64748b;
  --color-bg: #ffffff;
  --color-bg-section: #f0f7ff;
  --color-footer-bg: #0f2338;
  --font-display: 'Lexend', sans-serif;
  --font-body: 'Source Sans 3', sans-serif;
  --container-max: 1280px;
  --container-padding: clamp(1rem, 4vw, 2rem);
  --z-base: 0;
  --z-card: 10;
  --z-dropdown: 20;
  --z-header: 40;
  --z-mobile-cta: 50;
  --z-modal: 60;
  --z-toast: 100;
}
```

### Hard Rules (must satisfy in every phase)
- **Phone numbers**: every instance must be `<a href="tel:9166122126">(916) 612-2126</a>` — never plain text
- **Link contrast**: `--color-primary-light` (#2980b9) links must have `text-decoration: underline`
- **Accent buttons**: `--color-accent` with white text qualifies as large text only (Lexend 700 ≥16px)
- **Focus rings**: `outline: 2px solid #ea580c; outline-offset: 2px` on all interactive elements
- **Reduced motion**: `@media (prefers-reduced-motion: reduce)` disables all transitions
- **Mobile padding**: `padding-bottom: 56px` on `<body>` via mobile media query (offset for sticky bar)

---

## Build Phases

| Phase | Task | Commit Message |
|-------|------|----------------|
| B1 | Scaffold Astro + Tailwind v4 + install deps + globals.css tokens | `feat: scaffold Astro project with design system tokens` |
| B2 | 14 shared components (Layout, Header, Footer, MobileStickyBar, EmergencyBand, Button, LeadCaptureForm, HeroSection, ServicesGrid, TrustSignalsBar, TestimonialsSection, ServiceAreaSection, OfferSection, FAQAccordion) | `feat: add shared layout and UI components` |
| B3 | Homepage (`src/pages/index.astro`) with all 8 sections | `feat: build homepage with all conversion sections` |
| B4 | 23 inner pages (services hub, 8 service pages, service-areas hub, 8 city pages, about, blog, contact, privacy, terms) | `feat: add inner pages (services, about, contact, service areas)` |
| B5 | SEO layer (meta, OG, JSON-LD on homepage, sitemap.xml, robots.txt) | `feat: add SEO layer (meta tags, LocalBusiness schema, sitemap)` |
| B6 | Skipped (auth_enabled=false) | — |
| B7 | netlify.toml, .gitignore verify, `npm run build` pass | `feat: add deployment config and deploy prep` |

---

## Folder Structure

```
/
├── src/
│   ├── layouts/
│   │   └── Layout.astro
│   ├── components/
│   │   ├── EmergencyBand.astro
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── MobileStickyBar.astro
│   │   ├── Button.astro
│   │   ├── LeadCaptureForm.astro
│   │   ├── HeroSection.astro
│   │   ├── ServicesGrid.astro
│   │   ├── TrustSignalsBar.astro
│   │   ├── TestimonialsSection.astro
│   │   ├── ServiceAreaSection.astro
│   │   ├── OfferSection.astro
│   │   └── FAQAccordion.astro
│   ├── pages/
│   │   ├── index.astro
│   │   ├── about.astro
│   │   ├── contact.astro
│   │   ├── privacy.astro
│   │   ├── terms.astro
│   │   ├── blog/
│   │   │   └── index.astro
│   │   ├── services/
│   │   │   ├── index.astro
│   │   │   ├── drain-cleaning.astro
│   │   │   ├── water-heater.astro
│   │   │   ├── leak-detection.astro
│   │   │   ├── repiping.astro
│   │   │   ├── emergency-plumbing.astro
│   │   │   ├── bathroom-kitchen-plumbing.astro
│   │   │   ├── fixture-installation.astro
│   │   │   └── sewer-line.astro
│   │   └── service-areas/
│   │       ├── index.astro
│   │       ├── vacaville.astro
│   │       ├── fairfield.astro
│   │       ├── dixon.astro
│   │       ├── napa.astro
│   │       ├── vallejo.astro
│   │       ├── woodland.astro
│   │       ├── davis.astro
│   │       └── winters.astro
│   └── styles/
│       └── globals.css
├── public/
│   ├── sitemap.xml
│   ├── robots.txt
│   └── og-image.png       (placeholder)
├── .env.example
├── netlify.toml
├── astro.config.mjs
└── package.json
```

---

## Open Items (client TBDs — do not block build)

These fields are required before launch. Use placeholder values during build and flag in code comments.

| Item | Where Used | Status |
|------|-----------|--------|
| Street address + ZIP | JSON-LD schema, footer | TBD from client |
| Google Business Profile URL | JSON-LD `sameAs`, footer social | TBD from client |
| Yelp, Facebook URLs | Footer social links | TBD from client |
| Business hours (Sat/Sun) | JSON-LD `openingHours` | TBD from client |
| Logo image | `public/logo.svg` or header wordmark | Build with text wordmark; swap later |
| Real testimonials | `TestimonialsSection` | TBD — placeholder quotes in copy.json |
| Site URL (post-deploy) | `sitemap.xml`, canonical tags, OG URLs | `https://www.vacavilleplumbing.com` used as placeholder |
| Hero background photo | `HeroSection` background | Use gradient-only fallback during build |
