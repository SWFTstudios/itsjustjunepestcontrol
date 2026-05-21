# It's Just June Pest Control — Project Instructions

Read this file at the start of each session before making changes.

## Project summary

| Field | Value |
|-------|-------|
| **Client** | Junior Solice — founder of It's Just June Pest Control |
| **Agency / repo owner** | [SWFTstudios](https://github.com/SWFTstudios) |
| **Purpose** | Marketing landing page: same-day pest control in Bergen County, NJ |
| **Repository** | https://github.com/SWFTstudios/itsjustjunepestcontrol.git |
| **Stack** | Vanilla HTML, CSS, and JavaScript — no framework, no build step |

The site was originally built in Claude and is maintained in Cursor for coding and agent workflows.

## How to run locally

From the repo root:

```bash
# Option A — open directly
open index.html

# Option B — local server (recommended for relative asset paths after split)
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Directory layout

**Current:**

```
itsjustjunepestcontrol/
├── index.html          # monolith: embedded CSS + inline JS (~1,400 lines)
├── INSTRUCTIONS.md
└── .cursor/rules/      # Cursor agent rules
```

**Target (when splitting):**

```
itsjustjunepestcontrol/
├── index.html
├── INSTRUCTIONS.md
├── .cursor/rules/
└── assets/
    ├── css/main.css
    ├── js/main.js
    ├── js/config.js    # optional: phone, email constants
    └── images/
        ├── technician-hero.jpg
        └── junior-photo.jpg
```

See `.cursor/rules/asset-migration.mdc` for extraction steps.

## Page structure (`index.html`)

| Section ID | Purpose |
|------------|---------|
| `#hero` | Headline, CTAs, trust badges, hero photo placeholder |
| `#services` | Six service cards (rodents, bed bugs, cockroaches, wasps, ants, quarterly plan) |
| `#testimonials` | Google-style review marquee |
| `#areas` | Bergen County towns served |
| `#how` | Three-step process |
| `#why` | Value props + Junior quote |
| `#about` | Founder bio + photo placeholder |
| `#quoteModal` | Book appointment form (modal) |

**Primary CTAs:** `openModal()`, `tel:+12015550000`, `btn-gold` (call/book).

**Live preview:** https://itsjustjunepestcontrol.pages.dev/

## Mobile UX conventions

- **Breakpoints:** 479px (sm), 767px (md), 1023px (lg), 1024px+ (desktop)
- **Mobile (≤767px):** Phone-first — gold Call CTA before Book; sticky `#mobileCtaBar` (Call + Book); hamburger `#navDrawer`; hide `#floatCta`
- **Desktop:** Book + “or call” in hero; full nav links; floating call pill after scroll
- **Touch:** Buttons min 48px height; test at 320, 375, 768, 1024, 1440px widths

## Contact & placeholders

| Item | Status |
|------|--------|
| Email `hello@itsjustjune.com` | Set in markup |
| Phone `(201) 555-0000` / `tel:+12015550000` | **Placeholder** — replace everywhere before launch |
| Hero / about photos | Emoji placeholders — replace with real images |
| Quote form | Mock submit only (`handleSubmit` — no backend) |
| Privacy / Terms footer links | Stub `#` hrefs |

## Active to-do list

- [ ] **P0** — Replace placeholder phone in all `tel:` links and visible text (consider `assets/js/config.js` after split)
- [ ] **P0** — Add real images: `technician-hero.jpg`, `junior-photo.jpg` under `assets/images/`
- [ ] **P1** — Wire quote form to a backend (Formspree, Resend, etc.); add `name` attributes on inputs
- [ ] **P1** — Add `privacy.html` and `terms.html`; update footer links
- [ ] **P2** — Extract CSS/JS from `index.html` into `assets/` (see asset-migration rule)
- [ ] **P3** — Optional: favicon, Open Graph meta, `sitemap.xml`, analytics

## Do not change without asking

- Brand name spelling: **It's Just June** (not "Its Just June")
- Core `:root` color tokens (`--primary`, `--secondary-cont`, `--lime`, etc.)
- People-first, direct copy tone (no corporate jargon)

## Git workflow

- Remote: `origin` → `https://github.com/SWFTstudios/itsjustjunepestcontrol.git`
- Branch: `main`
- **Commit only when the user explicitly asks**
- Do not force-push to `main`

## Cursor rules

Agent guidance lives in `.cursor/rules/*.mdc`:

- `project-context.mdc` — always applied
- `design-system.mdc`, `html-structure.mdc`, `vanilla-js.mdc` — file-specific
- `asset-migration.mdc` — monolith → `assets/` split
