# P2P Dojo — AI Website Build Guide

**Purpose:** Handoff instructions for Agent B (OmegaGO) to build a 50-site website catalog from Agent A (ChatGPT) design specifications.

**Source:** `Untitled document (1).txt`, the reconstructed technical exchange between Agent A and Agent B. This is **not** a verbatim transcript. The ClearFlow code in that document was assembled and corrected from three partial OmegaGO outputs. Do not treat any unverified integrations, deployments, costs, credentials, reviews, or contact information as real.

## 1. Mission and roles

- **Agent A — ChatGPT:** Design direction, site concepts, brand tokens, content hierarchy, image prompts, QA and documentation.
- **Agent B — OmegaGO:** Implement accessible responsive pages, transform approved designs into generator-compatible structured data, test code, and deploy only when access and requirements are confirmed.
- **Human reviewer:** Approve content, supply actual business details, verify functionality and authorize deployments.

**Target:** 10 business niches × 5 website archetypes = **50 unique combinations**.

### Niches
Plumbing, Roofing, HVAC, Security, Construction, Med Spa, Legal, Dental, Restaurants, Real Estate.

### Archetypes
1. Lead-generation landing page
2. Multi-page brochure
3. Client portal/dashboard
4. Booking/quote funnel
5. Authority/blog hub

Every niche should eventually have all five archetypes. The current record contains **one assembled demo website**, not 50 finished sites.

## 2. Brand tokens

| Niche | Primary | Accent | Fonts |
|---|---|---|---|
| Plumbing | `#0B1F3A` | `#C9A227` | Manrope / Inter |
| Roofing | `#243447` | `#E87535` | Montserrat / Inter |
| HVAC | `#14243A` | `#24A6B8` | Inter |
| Security | `#111827` | `#D4AF37` | Rajdhani / Inter |
| Construction | `#20272B` | `#D97736` | Plus Jakarta Sans / Inter |
| Med Spa | `#28483E` | `#D8BD91` | Playfair Display / DM Sans |
| Legal | `#182C46` | `#B9975B` | Libre Baskerville / Inter |
| Dental | `#135C62` | `#BCE5D9` | Manrope / Source Sans 3 |
| Restaurants | `#45291F` | `#C58A52` | Cormorant Garamond / Lato |
| Real Estate | `#172B3A` | `#BDA47C` | DM Sans / Inter |

The ClearFlow CTA orange is `#D97721`. Other brand tokens should be confirmed per project before implementation.

## 3. Five featured concepts

| ID | Name | Archetype | Headline |
|---|---|---|---|
| `plumbing-leadgen-01` | ClearFlow Plumbing | Lead generation | Plumbing Problems? We're Ready When You Need Us. |
| `construction-brochure-01` | Stonebridge Builders | Brochure | Built with Purpose. Crafted to Last. |
| `hvac-portal-01` | ClimaCore Services | Client portal | Welcome Back to ClimaCore |
| `medspa-booking-01` | Solenne Aesthetics | Booking funnel | Your Moment to Feel Renewed. |
| `dental-authority-01` | BrightOak Dental | Authority hub | Better Dental Health Starts with Understanding. |

### Reference images

- ClearFlow design 1: https://i.postimg.cc/3Rr6DLk5/Clear-Flow-Plumbing-Homepage-Mockup.png
- ClearFlow design 2: https://i.postimg.cc/dV8SNMdv/Clear-Flow-Plumbing-Homepage-Mockup-(1).png
- Solenne: https://i.postimg.cc/zB3sct8p/Solenne-Aesthetics-Luxury-Landing-Page.png
- ClimaCore: https://i.postimg.cc/CMnyCQv5/Clima-Core-HVAC-Service-Dashboard.png

These are visual references, not verified production assets. OmegaGO reportedly preferred **ClearFlow design 1** for stronger CTA hierarchy. There is no confirmed Stonebridge or BrightOak image in the supplied record.

## 4. Start with three training builds

### Build A — ClearFlow Plumbing
- Use navy/gold/orange palette.
- Responsive sticky navigation; hero; call-to-action; trust strip; six service cards; example reviews; service areas; estimate form; footer.
- Use the existing **`index.html`** from the project as a *demo baseline*. It includes Tailwind CDN, Font Awesome, responsive menu, and a client-side demonstration form.
- **Do not say the form sends leads:** it does not connect to a backend or GoHighLevel. Do not publish fictional reviews, phone numbers, locations, or credentials as genuine.

### Build B — ClimaCore Services
- Navy/cyan client portal: sidebar, service summary cards, appointment/history area, support panel.
- Dashboard must use clearly labeled mock data until real authentication and data integrations exist.
- Fix any responsive overlaps and test keyboard navigation.

### Build C — Solenne Aesthetics
- Forest/champagne/ivory luxury booking experience.
- Treatment/service gallery, benefits, booking steps, FAQs, clear booking CTA.
- Booking must remain a mockup until a real scheduling provider and confirmation flow are connected.

## 5. Reusable component plan

Create configurable components rather than duplicating entire pages:

- `HeaderNav` and `MobileNav`
- `Hero_V1`
- `TrustStrip`
- `ServiceGrid_V1`
- `Testimonials` (only verified claims for live sites)
- `BookingForm_V1` (mock or real mode explicitly distinguished)
- `DashboardCards_V1`
- `FAQ`, `BlogPreview`, `ServiceAreas`, `Footer`

Each component should accept content, theme tokens, layout options and accessibility labels. Keep content separate from styling.

## 6. Structured data contract — verify before coding the generator

The original record contains **two different proposed JSON shapes**. Neither is confirmed as the real OmegaGO/P2P generator API. Do not silently assume compatibility.

The earlier proposed shape was:

```json
{
  "project_id": "plumbing-leadgen-01",
  "niche": "plumbing",
  "layout_type": "lead_gen",
  "branding": {
    "primary_color": "#0B1F3A",
    "secondary_color": "#C9A227",
    "font_family": "Manrope"
  },
  "content": {
    "hero": {
      "headline": "Plumbing Problems? We're Ready When You Need Us.",
      "subtext": "Demo copy — replace with approved business information.",
      "cta": "Request a Quote",
      "image_url": ""
    },
    "sections": []
  },
  "deployment": {
    "cloudflare_zone": "",
    "ghl_snapshot_id": ""
  }
}
```

A later proposal used `project_id`, `layout`, `components`, `theme`. **Action:** Ask OmegaGO for its actual schema, a minimal working input, expected output and validation rules. Only then generate all 50 site records.

## 7. Implementation workflow

1. **Confirm the schema and runtime.** Ask OmegaGO what it can execute, where files are stored, and which deployment credentials or APIs are actually available.
2. **Implement ClearFlow first.** Use the assembled `index.html` as reference; verify layout against ClearFlow design 1.
3. **Run local QA.** Check mobile, tablet, desktop; links; menu; form demo messaging; missing images; console errors; accessibility and performance.
4. **Implement ClimaCore and Solenne** as distinct archetypes, not simple recolors of ClearFlow.
5. **Extract reusable components** and build a theme/content configuration system.
6. **Create the remaining 47 site configurations** systematically (one row per niche × archetype).
7. **Review every site** for unique copy, relevant sections, responsive behavior and accurate claims.
8. **Deploy only after approval** to a confirmed Cloudflare or other hosting account. Keep preview and production URLs distinct.
9. **Integrate GoHighLevel only with real credentials and explicit permission.** Verify consent, contact creation, pipeline mapping, booking confirmations and failure handling.
10. **Document the final builds** with file paths, setup commands, deployment steps, screenshots and known limitations.

## 8. GoHighLevel training course — proposed outline

1. **Niche Blueprint:** Choose industry, audience, offer and website goal.
2. **High-Conversion Layouts:** Explain five archetypes, page hierarchy and CTA placement.
3. **Asset Generation:** Prepare brand tokens, imagery, copy and quality checks.
4. **Pipeline Build:** Demonstrate GHL contacts, forms, workflows, calendars and pipelines in a test environment.
5. **Deployment & Scaling:** Publish safely, test conversion paths, duplicate configurations and maintain sites.

Use ClearFlow, ClimaCore and Solenne as practical rebuild exercises. The record does **not** establish that the GHL course or integrations have already been implemented.

## 9. QA and acceptance checklist

- [ ] Correct niche and archetype; unique design and relevant content
- [ ] Approved brand colors, typography, assets and copy
- [ ] Responsive at phone, tablet and desktop widths
- [ ] Keyboard-accessible navigation, semantic headings, form labels and alt text
- [ ] All navigation and CTA links tested
- [ ] Forms explicitly marked as **demo** or tested end-to-end with real destination
- [ ] No fabricated testimonials, licensing claims, ratings or business contact details
- [ ] No secrets or API keys embedded in client-side HTML/JSON
- [ ] External images and dependencies load, with fallbacks where appropriate
- [ ] Console and network errors checked
- [ ] Human approval recorded before production deployment
- [ ] Deployment URL and source files documented when actually available

## 10. Short prompts to send OmegaGO (avoid context overflow)

The OmegaGO session reportedly hit an **8,192-token context limit**. Work in fresh chats or small, focused requests. Do not paste the entire 50-site brief and full source code at once.

**Prompt 1 — Validate generator**
> We are building a 50-site catalog: 10 niches × 5 archetypes. Before implementation, provide your actual accepted generator JSON schema, one minimal valid example, and tell me whether you can execute code and deploy. Do not assume a schema from our previous discussion.

**Prompt 2 — ClearFlow implementation**
> Build or validate the ClearFlow Plumbing lead-generation demo using navy #0B1F3A, gold #C9A227, orange CTA #D97721. Sections: responsive nav, hero, trust strip, six services, demo testimonials, service areas, demo estimate form and footer. Keep demo claims clearly labeled; do not claim GHL integration. Return only the files or changes needed for this build.

**Prompt 3 — Test report**
> Review the ClearFlow implementation. Report what you actually tested, what you could not test, broken links, accessibility issues, form behavior, and exact remaining steps before deployment. Do not claim it is live without a verified URL.

## 11. Suggested shared folder structure

```text
P2P-Dojo/
  transcript/
    P2P_Dojo_ChatGPT_OmegaGO_With_Code.txt
  docs/
    P2P_Dojo_AI_Website_Build_Guide.md
  websites/
    clearflow/
      index.html
  references/
    clearflow-design-1.png
    clearflow-design-2.png
    solenne.png
    climacore.png
  outputs/
    previews/
    test-reports/
```

Filenames for reference images are suggestions, not proof the files are already in the folder.

## 12. Unresolved items requiring confirmation

- Full original Agent A and Agent B transcript, if the teacher requires verbatim chat exports.
- The actual OmegaGO generator schema and execution/deployment capabilities.
- Whether the 50 sites are static demos, full applications, or client-ready production websites.
- Real business content, contact information, media rights and approved claims.
- Real GHL account, forms, calendar, workflows and pipeline specifications.
- Hosting ownership, domain names, Cloudflare access and security requirements.
- Course deliverable format and assessment requirements.

**Current milestone:** Reconstructed AI technical record and one assembled ClearFlow demo codebase exist. The next practical milestone is verifying OmegaGO's schema and completing/test-reporting the ClearFlow demo before scaling.
