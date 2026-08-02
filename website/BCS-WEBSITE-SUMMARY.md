# Benchmark Contract Services Website — Full Summary

## Read this first: likely why your engineer can't use it

The site was built inside **`swissbelt/superpowers`**, on branch **`claude/bcs-website-redesign-ot3vff`**, in a `/website` subfolder. That repo is a **Claude Code plugin/skills framework** — an unrelated open-source tool with its own contribution rules, CI, and structure. It is not a website project, has no build tooling, and isn't a sensible place to deploy from.

This was flagged before any code was written, but building here was the explicit choice at the time rather than being given a proper repo to work in. That's almost certainly why your engineer says he can't use it — he'd be trying to deploy a website out of the middle of someone else's unrelated GitHub project, possibly one he doesn't even have access to.

**The actual fix:** move the `website/` folder into its own clean repository (or into whatever repo your engineer actually deploys from), so he has a normal, self-contained project to work with. I can do this — I just need to know where it should go (a new repo, an existing one, or you can pull the files yourself from the attached copy below).

## What was built

A 5-page static marketing site for Benchmark Contract Services (BCS), a Building Service Contractor:

- **Home** — routes visitors to Government / Private / Partner paths
- **Government Clients** — procurement-toned, audience list, why-BCS, services, delivery model, eVA vendor badge, quote form
- **Private Clients** — convenience-toned equivalent for property managers/commercial clients
- **Partner With Us** — subcontractor recruitment, Four-Gate Screening Process, application form
- **About** — mission, why-two-markets, founder-led philosophy, how BCS creates value

**Stack:** plain HTML5 + one CSS file + one JS file. No framework, no build step, no npm dependencies, no third-party CDN calls. Opens directly in a browser or serves from any static host (Netlify, Vercel, S3, GitHub Pages, etc.) with zero configuration.

**Design system:** navy (`#0b1a2c`) / gold (`#c6963c`) / cream (`#faf8f4`) palette, system font stack, hand-authored SVG icons (no icon library). The real BCS logo (from the file you uploaded) is wired into every header and footer, with a white backing plate so it stays legible on the navy footer. Favicon generated from the same artwork.

## Content sourcing — important caveat

All copy is derived from the task brief given in this session (a paraphrase of business-plan sections), **not from an actual BCS Business Plan document** — no such document was ever attached to or found in this session. **Content should be checked against the real plan before publishing.**

Otherwise followed strictly, with no fabricated stats, certifications, testimonials, client logos, awards, or years-in-business claims. Service lines: Janitorial, Landscaping, Pressure Washing, Hauling, Painting. Government page states "Active eVA Vendor" only. Partner page details the Four-Gate Screening Process (Insurance & Licensing, Capacity for Recurring Work, Alignment with the BCS Backend Model, Geographic Coverage).

## Known gaps before going live

1. **Forms don't submit anywhere.** The quote/application forms validate and show a success message client-side, but there's no backend or destination email wired up — needs a real endpoint.
2. **No real photography.** A few sections use small hand-drawn line-art SVG diagrams instead of photos (per a "no stock imagery" instruction). Swap in real photography if available.
3. **Business plan verification** — see above.
4. **No analytics/tracking.**
5. **Not deployed anywhere yet.**

## File structure

```
website/
  index.html          Home
  government.html     Government Clients
  private.html        Private Clients
  partner.html        Partner With Us
  about.html           About
  css/styles.css       Design system + all page styles
  js/main.js           Mobile nav, scroll-reveal, form handling
  assets/logo.png      BCS logo (transparent background)
  assets/favicon.png   Favicon generated from the logo
  robots.txt
  sitemap.xml
```

## Where to get the actual files

- **GitHub:** `swissbelt/superpowers`, branch `claude/bcs-website-redesign-ot3vff`, folder `/website`
- **Live clickable preview** (all 5 pages, merged into one demo for convenience — not the real file structure): https://claude.ai/code/artifact/0bacd41c-7223-48c5-9f98-6ec005848f80

## Revision history (what changed after first draft, and why)

1. **Initial build** — all 5 pages, design system, forms, SEO meta, sitemap/robots.txt.
2. **Bug fixes from testing:**
   - Several sections were missing a base CSS class, zeroing out their padding.
   - Mobile nav menu rendered corrupted because `backdrop-filter` on the sticky header broke fixed-position child positioning — removed the blur.
3. **Copy de-duplication** — the "one point of contact / scheduling / invoicing / subcontractor management / quality assurance" model was being restated three times per page (hero, feature grid, checklist) on Government, Private, and About. Trimmed to state it once per page.
4. **Fixed "empty tile" bug** — primary content blocks (forms, the About CTA banner) could render invisible if a scroll-reveal animation missed its trigger. Removed that animation from critical blocks and added a safety-net timeout.
5. **Filled empty illustration placeholders** with small diagrams (hub-and-spoke, converging paths, oversight diagram) instead of blank gradient boxes.
6. **Added the real logo**, replacing the placeholder text mark, plus a matching favicon.
7. **Removed all em dashes** from the copy, rewritten as separate sentences, commas, colons, or parentheses depending on what each sentence needed.
