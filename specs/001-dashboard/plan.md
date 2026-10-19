# Implementation Plan: Influencer Dashboard

## Goal

Implement the dashboard defined in [spec.md](spec.md) as a static, semantic HTML report styled exclusively with Tailwind CSS v4 utilities. Organize the page into outcomes, performance drivers, and operational details, with a compact header and native section navigation rather than a sidebar.

## 1. Foundation: Sample Data

- Use September 1-30, 2026 as the reporting period.
- Define six campaigns covering Instagram, TikTok, and YouTube, with each of Products A, B, and C represented on two platforms.
- Record campaign dates, product, platform, reach, impressions, clicks, available interaction counts, completed one-unit sales, and direct promotional costs.
- Preserve the specified prices: Product A EUR 50, Product B EUR 120, and Product C EUR 80, each with a 15% commission.
- Attribute every sale and cost once. Avoid shared costs in this prototype.
- Include varied performance and at least one negative-commission-ROI campaign to support meaningful observations.
- Calculate campaign, product, platform, and overall totals before populating the dashboard. Calculate aggregate rates from summed numerators and denominators.
- Keep deterministic source figures in an HTML comment alongside the report; no runtime dataset or application JavaScript is needed.
- Treat unsupported interaction types as unavailable rather than inventing values. Clearly label summed reach as non-deduplicated.

**Validation gate:** Dates fall within the reporting period, all required products and platforms are represented, conversions do not exceed clicks, clicks do not exceed reported reach, and commissions and costs reconcile.

## 2. Foundation: Semantic Shell and Visual Patterns

**Dependency:** Sample reporting metadata from stage 1.

- Add document language, descriptive title, viewport metadata, and the official Tailwind CSS v4 runtime: `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`.
- Add a visible-on-focus skip link, page header, labeled navigation, one `main` landmark, and three sections with IDs `outcomes`, `drivers`, and `operations`.
- Display dashboard identity, reporting period, and sample-data status in the header.
- Establish reusable utility-class patterns for widget borders, spacing, labels, numbers, tables, and focus indicators.
- Use a light neutral canvas, dark text, teal outcome accents, amber observations, and red negative results. Check contrast and pair status colors with text.
- Use Tailwind spacing, sizing, and fixed type-scale utilities without custom CSS, arbitrary pixel dimensions, nested cards, or framed page sections.
- Select one relevant, appropriately licensed local bitmap asset for the product view. Include meaningful alternative text and any required attribution. Do not imply a generic illustration is a photograph of an actual promoted product.

**Validation gate:** The page has a logical heading hierarchy, working section links, the permitted Tailwind v4 script only, and no custom styles or application scripts.

## 3. Top Block: Outcome KPIs

**Dependency:** Stages 1 and 2.

- Build four consistently structured widgets: commission income, completed sales, reach-based conversion rate, and engagement rate.
- Give each widget a label, primary value, and sufficient context to interpret the metric.
- Distinguish commission income from gross product sales value and make the non-deduplicated reach definition available.
- Use a single-column base grid, two columns at `sm:`, and four columns at `lg:`.
- Do not add previous-period arrows or trends without a supporting comparison dataset.

**Validation gate:** All four values match the campaign sample and remain readable without clipping at mobile and desktop widths.

## 4. Middle Block: Performance Drivers

**Dependency:** Stages 1 and 2. Can proceed alongside stage 3 once shared patterns are agreed.

- Build a conversion funnel showing reported reach, clicks, and completed sales, with explicitly labeled click/reach, sale/click, and sale/reach rates.
- Compare platform commission income, engagement rate, conversion rate, and commission return on spend. Identify the leader for each metric.
- Compare product commissions, sales, conversion rates, and engagement rates. Identify the highest-commission product.
- Prefer labeled lists or compact tables. If bars are included, use Tailwind utilities and preserve exact text values independently of bar length or color.
- Include the product-related visual asset without crowding the performance figures.
- Stack views on mobile, use a suitable two-column arrangement at `md:`, and present three views across at `lg:` where readable.

**Validation gate:** Three distinct driver views are present, rankings match the figures, and funnel rates use clearly identified denominators.

## 5. Bottom Block: Operational Details

**Dependency:** Stages 1 and 2. Can proceed alongside stages 3 and 4.

- Build the three operational tables with consistent styling, captions, `thead` and `tbody`, scoped row and column headers, and aligned numeric values.
- Products table: product, unit price, conversions, sales value, commissions, promotional costs, and commission ROI.
- Platforms table: platform, reported reach, interactions, engagement rate, conversions, conversion rate, commissions, costs, and commission return on spend.
- Campaigns table: campaign, dates, product, platform, conversions, commissions, costs, and commission ROI.
- Put each wide table in its own labeled, keyboard-focusable horizontal-scroll container. Prevent horizontal overflow of the page itself.
- Add at least two observations supported by displayed figures, including the negative-ROI campaign. Avoid historical spike, drop, or anomaly claims without baseline data.

**Validation gate:** All three tables have the required columns, totals reconcile with the KPI and driver blocks, and observations cite evidence from the report.

## 6. Integration and Documentation

**Dependency:** Stages 3-5.

- Harmonize spacing, typography, numeric precision, and status treatments across all sections.
- Complete mobile-first adaptations using `sm:`, `md:`, and `lg:` utilities; ensure navigation and reporting metadata wrap cleanly.
- Use consistent euro formatting, count separators, percentage precision, and return multiples. Display undefined ratios as N/A.
- Confirm section navigation and the skip link work, images load, and no controls falsely imply filtering, sorting, export, or live updates.
- Update the README with the dashboard scope, existing server command, Tailwind runtime network dependency, sample-data definitions, and any asset attribution.
- Keep the specification separate and unchanged. Reuse the existing Flask server without modifying its behavior.

**Validation gate:** The report reads as one coherent static dashboard and accurately describes its sample-data limitations.

## 7. Final Verification

**Dependency:** Stage 6.

- Run available HTML conformance checks and inspect the source for semantic landmarks, correct table structure, and the allowed Tailwind v4 setup.
- Confirm there is no Tailwind v3 CDN, custom CSS, additional styling framework, or application JavaScript.
- Independently recompute totals, 15% commissions, weighted rates, commission ROI, and commission return on spend from the source sample. Use an external calculation or manual worksheet, not dashboard JavaScript.
- Inspect approximately 375, 640, 768, and 1280 CSS-pixel viewports, including screenshots when browser tooling is available. These are verification sizes, not implementation dimensions.
- Check single/two/four-column KPI behavior, tablet driver wrapping, desktop driver arrangement, readable labels, local table scrolling, and absence of page overflow or overlapping content.
- Verify keyboard navigation, skip-link behavior, scroll-container accessibility, visible focus, heading structure, text contrast, image alternatives, and usability at 200% zoom.
- Serve the page through the existing development server for verification and provide its URL. Report any checks that available tooling cannot execute.

**Completion gate:** Four KPIs, three driver views, three operational tables, and two evidence-based observations meet the specification across mobile, tablet, and desktop.

## File Scope

| Path | Intended change |
| --- | --- |
| `index.html` | Semantic dashboard markup, embedded sample figures, Tailwind utilities, and canonical sample comment. |
| `assets/` | Required relevant bitmap asset; create only when adding the asset. |
| `README.md` | Actual running instructions, report scope, data definitions, and asset credit where required. |
| `server.py` | Reuse unchanged for local serving. |
| `specs/001-dashboard/spec.md` | Reference as the authoritative requirements; do not modify as part of implementation. |

## Exclusions

- No application JavaScript, custom CSS, charting libraries, frontend framework, or production CSS build.
- No new dependency manifests or persistent executable test infrastructure solely for this static report.
- No APIs, database, authentication, account connections, or automated data refresh.
- No interactive filters, sorting, export, or date-picker controls.
- No unsupported MRR, churn, NPS, CSAT, attendance, pass rates, or previous-period comparisons.
- No unique cross-platform audience claims or influencer ROI calculated from gross product sales value.