# Sahtein

**France-first marketplace for scheduled homemade Lebanese & Levantine meals.**

Sahtein is the **trust layer for homemade ethnic food**: diaspora and food lovers order authentic meals from independent local chefs — paid safely, fulfilled with proof, and easy to reorder. It is **not** an on-demand courier app and **not** a HACCP certification body. Chefs remain food-business operators; Sahtein guides, prevents incomplete selling, and operates the marketplace spine.

| | |
|---|---|
| **Org** | [Sahtein-Marketplace](https://github.com/Sahtein-Marketplace) |
| **Docs site (local)** | [http://127.0.0.1:3400/docs/intro](http://127.0.0.1:3400/docs/intro) |
| **Positioning** | Scheduled cook-days · chef pickup / self-delivery · trust & proof |
| **Launch focus** | Dense Paris / Île-de-France cells |

---

## GitHub short description (≤349 characters)

Copy into the repository **About** description:

```text
Sahtein is a France-first marketplace for scheduled homemade Lebanese & Levantine meals—a trust layer for independent chefs. Cook-days, safe Stripe pay, allergen passport, dual handoff proof, chef pickup/self-delivery. Not a courier app. Repos: Docs, Frontend, Backend, Design System. Figma Make + Design System. Paris launch · RGPD.
```

*(333 characters — under GitHub’s ~350 limit.)*

Suggested topics: `marketplace`, `foodtech`, `france`, `lebanese-food`, `medusa`, `nextjs`, `rgpd`, `product-docs`

---

## Objectives

| # | Objective | Product implication |
|---|---|---|
| **O1** | Differ from Uber Eats / generic delivery | Cook-day calendars, chef story, proof — no fleet theatre |
| **O2** | Raise 2nd & 3rd order probability | Favorites, one-tap reorder, dashboard pulse, consent-aware CRM |
| **O3** | Chefs reliable & economically successful | Day-of UX, capacity, Offer Studio, settlements, badges |
| **O4** | Data / community advantage | Dish graph, SEO chef profiles, city cells, marketing reuse layer |

**North-star metric:** weekly repeat orders per active chef.

**V1 must prove (Paris):** ~30–40 founding chefs · 2 dense cells · D30 repeat &gt;35% · refund/claim &lt;4% · 8+ orders/chef/week · NPS &gt;50.

Full strategy: [`website/docs/strategy/objectives.md`](website/docs/strategy/objectives.md)

---

## Platform in one paragraph

Customers discover dishes by **cook-day**, occasion, search, or chef; build a cart (including multi-chef); pay once on **Stripe** (auth → capture after chef accept). Chefs subscribe (€10/mo + commission), publish offers with portion truth and allergens, accept/counter/decline under SLA, prep, and complete **pickup or self-delivery** with dual handoff proof. Sahtein admin vets supply, runs support/refunds/finance, and growth tools. A dedicated **`marketing` schema/service** holds consent-aware profiles for ESP reuse — never allergy data, never Brevo-as-source-of-truth.

---

## Main features

### Customers
- Sign-up particulier / entreprise · addresses · Allergy Passport · cookie CMP  
- Cook-day marketplace · occasions · dish & chef passports · search  
- Cart & multi-chef checkout · fee lock · dual invoices  
- Order tracking (no fake GPS) · pickup codes · safe drop · masked chat  
- Favorites · reorder · ratings (plat + platform) · claims / refunds  

### Chefs
- Onboarding & compliance vault (admin gate before publish)  
- Menu / Dish Passport · calendar & capacity · vacation mode  
- Order inbox · accept / counter / decline · prep lists & labels  
- Pickup & self-delivery handoff · revenue & settlements view  
- Offer Studio (codes / BOGO interim) · chef marketing (own customers only)  

### Platform (admin)
- Vetting · catalogue (categories, dishes, occasions)  
- Orders 360 · support inbox · refunds with four-eyes where required  
- Fee plans · finance / Sirene · Control Tower  
- Growth: banners, newsletter, segments, ESP sync via marketing data service  

### Trust & money (non-negotiable)
- Silence never charges · fee lock · double-entry ledger  
- Masked chef↔customer contact · allergen hard blocks  
- Sahtein does **not** issue HACCP  

---

## Main product elements

| Element | Role |
|---|---|
| **Storefront** | Customer web (`app.` / apex) — discovery → checkout → tracking |
| **Back office** | Chef ops + Sahtein admin (`admin.`) |
| **API** | Medusa v2 modular monolith (`api.`) — OpenAPI `/api/v1` |
| **Worker** | Outbox, jobs, ESP sync, labels, projections |
| **PostgreSQL** | System of record + schema `marketing` for audience reuse |
| **Keycloak** | OIDC + PKCE identity |
| **Stripe** | Customer pay on platform account; V1 chef payouts manual admin |
| **Brevo** | Transactional + marketing email (synced from marketing schema) |
| **Docs site** | Docusaurus — product & architecture source of truth |

---

## Repositories

All under **[github.com/Sahtein-Marketplace](https://github.com/Sahtein-Marketplace)**.

| Repository | What it is | Clone |
|---|---|---|
| **[Sahtein-Docs](https://github.com/Sahtein-Marketplace/Sahtein-Docs)** *(this repo)* | Product, legal, workflows, architecture, ADRs, design briefs — **implementation SoT** | `git clone git@github.com:Sahtein-Marketplace/Sahtein-Docs.git` |
| **[Sahtein-Frontend](https://github.com/Sahtein-Marketplace/Sahtein-Frontend)** | Next.js storefront + admin · design tokens · i18n · Storybook | `git clone git@github.com:Sahtein-Marketplace/Sahtein-Frontend.git` |
| **[Sahtein-Backend](https://github.com/Sahtein-Marketplace/Sahtein-Backend)** | Medusa API + worker · contracts · platform/identity packages | `git clone git@github.com:Sahtein-Marketplace/Sahtein-Backend.git` |
| **[Sahtein_DesignSystem](https://github.com/Sahtein-Marketplace/Sahtein_DesignSystem)** | Figma Make UI prototype export · living DS reference (not production API) | `git clone git@github.com:Sahtein-Marketplace/Sahtein_DesignSystem.git` |

### How to access each repo

1. Request org membership / team access from a Sahtein-Marketplace admin.  
2. Clone with SSH (preferred) or HTTPS using a PAT with `repo` scope.  
3. Read **this Docs repo first** (`website/` + `build/`) before changing product behaviour.  
4. Frontend & Backend: Node **24 LTS** + **pnpm 9.15.9** (see each repo `.nvmrc`).  
5. Architecture and build plan: `Sahtein-Docs/build/` — do not invent parallel ADRs in app repos.

```bash
# Typical local layout
mkdir -p ~/Dev/Sahtein && cd ~/Dev/Sahtein
git clone git@github.com:Sahtein-Marketplace/Sahtein-Docs.git
git clone git@github.com:Sahtein-Marketplace/Sahtein-Frontend.git
git clone git@github.com:Sahtein-Marketplace/Sahtein-Backend.git
git clone git@github.com:Sahtein-Marketplace/Sahtein_DesignSystem.git
```

---

## Design & Figma

| Asset | Link | Use |
|---|---|---|
| **Figma Make — Sahtein** | [figma.com/make/…/Sahtein](https://www.figma.com/make/JYfEpYxY9ViQhG0avMgU7K/Sahtein) | Interactive prototype / Make source (customer · chef · admin screens) |
| **Figma Design — DS & screens** | [figma.com/design/EXdNZEOgW2wesDIp2NVqaL](https://www.figma.com/design/EXdNZEOgW2wesDIp2NVqaL) | Design system & screen frames (Nov 2026 workflow audit) |
| **Make prompt (docs)** | [`website/docs/product/figma-make-prompt.mdx`](website/docs/product/figma-make-prompt.mdx) | Copy-paste prompt for regenerating / extending Make |
| **UX/UI screen brief** | [`website/docs/product/ux-ui-screen-brief.mdx`](website/docs/product/ux-ui-screen-brief.mdx) | Screen inventory & V1 cut |
| **Designer inventory** | [`UX-UI-DESIGNER-INVENTORY.md`](UX-UI-DESIGNER-INVENTORY.md) | Full catalogue for design coverage |
| **DS repo** | [Sahtein_DesignSystem](https://github.com/Sahtein-Marketplace/Sahtein_DesignSystem) | Code export of Make; production UI is ported into `Sahtein-Frontend/packages/ui` |

**Rule (D-076 / D-010):** Figma Make is visual and copy reference. Port tokens and reviewed patterns into Frontend; do not treat Make as the production app.

---

## Docs site (this repository)

```bash
cd website
npm install
npm start      # http://127.0.0.1:3400
npm run build
npm run serve
```

| Path | Role |
|---|---|
| `website/` | **Implementation source of truth** (Docusaurus) |
| `build/` | Build plan, progress, ADRs, production readiness |
| `design/` | Design-system charter & UX briefs |
| `SAHTEIN_Master_Product_Spec_v2_1.md` | Historical atomic archive — website wins on conflict |

---

## Licence (suggestion)

Sahtein is a **commercial marketplace product**. Recommended default until counsel decides otherwise:

| Scope | Suggested licence |
|---|---|
| **Application code** (Frontend, Backend, DesignSystem) | **Proprietary — All Rights Reserved** (no public open-source grant) |
| **This Docs repo** (if shared externally later) | Same proprietary default, **or** `CC BY-NC-ND 4.0` for published product docs only |
| **GitHub UI field** | Set licence to **“Other” / no OSI licence** and add a root `LICENSE` stating proprietary ownership |

**Do not** publish as MIT/Apache until IP, brand, and supplier contracts are cleared. Add a short `LICENSE` file in each repo, for example:

```text
Copyright (c) Sahtein / Sahtein-Marketplace. All rights reserved.
Unauthorised copying, distribution, or use of this software and documentation
via any medium is strictly prohibited without prior written permission.
```

SPDX-style marker for private packages: `LicenseRef-Sahtein-Proprietary`.

---

## Brand (docs / product)

| Role | Token | Hex |
|---|---|---|
| Brand / primary | herb | `#5A7A55` |
| Accent CTA | terra | `#D95F35` |
| Highlight | saffron | `#D4A843` |
| Canvas | cream | `#FBF6EE` |
| Ink | charcoal | `#231A12` |

Fonts: **Fraunces** (display) · **DM Sans** (body).

---

## Contact & ownership

Product and architecture decisions for V1 live in this Docs site. When Master Spec / Delta conflict with `website/`, **prefer the website**.
