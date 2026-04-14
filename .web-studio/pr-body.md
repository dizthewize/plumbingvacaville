# PR: feat: Vacaville Plumbing — initial site build

## Summary
- 24-page Astro 6 (static) site built from design system and site plan
- 14 shared components (Header, Footer, MobileStickyBar, LeadCaptureForm, HeroSection, ServicesGrid, TrustSignalsBar, TestimonialsSection, OfferSection, FAQAccordion, ServiceAreaSection, Button, EmergencyBand, Layout)
- Auth: not included (service site MVP)

## Pages Built
- `/` — Homepage with all 8 conversion sections + LocalBusiness JSON-LD schema
- `/services` — Services hub
- `/services/drain-cleaning`, `/services/water-heater`, `/services/leak-detection`, `/services/repiping` — Service pages
- `/services/emergency-plumbing` — Phone-first emergency page (primary CTA is tel: link, 24/7)
- `/services/bathroom-kitchen-plumbing`, `/services/fixture-installation`, `/services/sewer-line` — Service pages
- `/service-areas` — Hub with 8 city cards
- `/service-areas/vacaville`, `/fairfield`, `/dixon`, `/napa`, `/vallejo`, `/woodland`, `/davis`, `/winters` — City pages
- `/about` — About page with values grid
- `/contact` — Contact page with form + hours
- `/blog` — Blog placeholder
- `/privacy`, `/terms` — Legal pages

## Build status
- npm run build passes — 24 pages, 0 errors, 0 warnings

## Before Launch (Client TBDs)
- Replace placeholder testimonials with real customer reviews
- Add streetAddress + postalCode to JSON-LD schema and contact page
- Add social profile URLs (Google Business, Yelp, Facebook) to sameAs in schema
- Upload logo image and og-image.png
- Confirm Saturday/Sunday hours for schema and contact page

---
Note: PR creation skipped — initial build was committed directly to main (no base branch exists).
To create a PR for future changes, work on a feature branch and push before running gh pr create.
