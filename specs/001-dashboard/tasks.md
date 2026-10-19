# Dashboard Implementation Tasks

Based on [plan.md](plan.md) and governed by [spec.md](spec.md). Tasks are executed in order and checked only after completion and verification.

## 1. Foundation: Sample Data

- [x] T001 Set the reporting period to September 1-30, 2026.
- [x] T002 Define six campaigns spanning Instagram, TikTok, and YouTube, with each product represented on two platforms.
- [x] T003 Assign each campaign dates, product, platform, and direct promotional costs without duplicating sales or costs.
- [x] T004 Add campaign reach, impressions, clicks, completed one-unit sales, and available interaction counts; mark unsupported types unavailable.
- [x] T005 Apply Product A/B/C prices of EUR 50/120/80 and the 15% commission rate.
- [x] T006 Calculate campaign sales value, commission income, commission ROI, and commission return on spend; include a negative-ROI campaign.
- [x] T007 Calculate product and platform aggregates, including interactions, engagement rates, and reach-based conversion rates.
- [x] T008 Calculate overall KPI totals and rates from summed numerators and denominators, not averaged percentages.
- [x] T009 Preserve the canonical sample figures in an HTML comment beside the report.
- [x] T010 Check campaign dates, product/platform coverage, conversions <= clicks <= reach, and reconciliation of sales, commissions, and costs.

## 2. Foundation: Semantic Shell and Visual Patterns

Depends on stage 1 reporting metadata.

- [x] T011 Add the HTML document structure, language, descriptive page title, and viewport metadata.
- [x] T012 Load only the permitted Tailwind v4 runtime: `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`.
- [x] T013 Add a visible-on-focus skip link targeting the main content.
- [x] T014 Build the header with dashboard identity, reporting period, and sample-data status.
- [x] T015 Add labeled native navigation linking to `outcomes`, `drivers`, and `operations`.
- [x] T016 Add one `main` landmark and the three ordered sections with a logical heading hierarchy.
- [x] T017 Establish matching Tailwind utility patterns for widgets, spacing, labels, numbers, borders, and focus indicators.
- [x] T018 Apply the planned neutral, teal, amber, and red palette with text labels for status and accessible contrast.
- [x] T019 Add an appropriately licensed relevant bitmap under `assets/`, with accurate alternative text and recorded attribution requirements.
- [x] T020 Check section links, document outline, and absence of custom CSS, arbitrary pixel dimensions, nested cards, or application scripts.

## 3. Top Block: Outcome KPIs

Depends on stages 1 and 2.

- [x] T021 Build a commission-income widget that clearly distinguishes earned commission from gross sales value.
- [x] T022 Build a completed-sales widget using the reconciled conversion total.
- [x] T023 Build a reach-based conversion-rate widget with denominator context.
- [x] T024 Build an engagement-rate widget using interactions divided by reported reach.
- [x] T025 Apply the same label/value/context structure to all four widgets and make non-deduplicated reach terminology available.
- [x] T026 Set the KPI grid to one base column, two at `sm:`, and four at `lg:`.
- [x] T027 Check all four values against the sample and verify readable labels without unsupported trend indicators.

## 4. Middle Block: Performance Drivers

Depends on stages 1 and 2; can proceed alongside stage 3 after shared patterns are established.

- [x] T028 Build funnel counts for reported reach, clicks, and completed sales.
- [x] T029 Label click/reach, sale/click, and sale/reach rates explicitly.
- [x] T030 Build platform comparisons for commissions, engagement, conversion, and commission return on spend.
- [x] T031 Identify the strongest platform separately for each comparison metric.
- [x] T032 Build product comparisons for commissions, sales, conversion, and engagement; identify the commission leader.
- [x] T033 Add the selected visual asset to the product view without implying it depicts an actual product unless appropriate.
- [x] T034 Keep comparison values available as text; use only HTML and Tailwind utilities for any visual bars.
- [x] T035 Stack driver views on mobile, adapt at `md:`, and arrange three across at `lg:` where readable.
- [x] T036 Check all three driver views against the source figures, including ranking accuracy and rate denominators.

## 5. Bottom Block: Operational Details

Depends on stages 1 and 2; can proceed alongside stages 3 and 4.

- [x] T037 Build the products table with product, unit price, conversions, sales value, commissions, costs, and commission ROI.
- [x] T038 Build the platforms table with platform, reported reach, interactions, engagement, conversions, conversion rate, commissions, costs, and commission return on spend.
- [x] T039 Build the campaigns table with campaign, dates, product, platform, conversions, commissions, costs, and commission ROI.
- [x] T040 Add captions, table head/body groups, scoped row/column headers, and consistent numeric alignment to each table.
- [x] T041 Wrap each wide table in its own labeled, keyboard-focusable horizontal-scroll container.
- [x] T042 Add an observation supported by the negative-ROI campaign's displayed figures.
- [x] T043 Add a second current-period improvement opportunity supported by specific displayed figures, without unsupported historical claims.
- [x] T044 Check required columns, row values, aggregate reconciliation, observation accuracy, and table-local rather than page-level overflow.

## 6. Integration and Documentation

Depends on stages 3-5.

- [x] T045 Harmonize spacing, typography, status treatments, euro formatting, count separators, percentages, and return multiples across blocks.
- [x] T046 Display undefined ratios as N/A rather than zero or infinity, rounding only displayed values.
- [x] T047 Complete mobile-first `sm:`, `md:`, and `lg:` adaptations, including clean wrapping of navigation and header metadata.
- [x] T048 Confirm image rendering, skip-link behavior, and native section navigation; remove any controls suggesting unsupported interactivity.
- [x] T049 Update the README with scope, the existing server command, sample definitions, runtime network dependency, and required asset credit.
- [x] T050 Check that sample status, non-deduplicated reach, attribution, and commission-based return definitions are consistent throughout.
- [x] T051 Confirm implementation changes stay within the planned file scope; leave the specification and server behavior unchanged.

## 7. Final Verification

Depends on stage 6. Record any checks unavailable in the environment rather than marking them passed.

- [x] T052 Run available HTML conformance checks and inspect landmarks, heading hierarchy, captions, and header scopes.
- [x] T053 Verify the sole script is the permitted v4 runtime and there is no `cdn.tailwindcss.com`, custom CSS, additional styling framework, or application JavaScript.
- [x] T054 Independently recalculate totals, 15% commissions, weighted rates, commission ROI, and commission return on spend outside the dashboard.
- [x] T055 Serve the page using the existing development server without modifying its behavior.
- [x] T056 Inspect at approximately 375 CSS pixels: verify stacked widgets, wrapping, readable content, and no page overflow.
- [x] T057 Inspect around 640 CSS pixels: verify the `sm:` transition and two-column KPI layout.
- [x] T058 Inspect at approximately 768 CSS pixels: verify tablet driver arrangement and readable table scrolling.
- [x] T059 Inspect at approximately 1280 CSS pixels: verify four KPI columns and three driver views across where readable.
- [x] T060 Capture responsive screenshots when browser tooling is available; check asset loading, clipped text, and overlaps.
- [x] T061 Test keyboard access to the skip link, navigation, and table scrolling, including visible focus indicators.
- [x] T062 Check text contrast, non-color status labels, meaningful image alternatives, and usability at 200% zoom.
- [x] T063 Confirm all four KPIs, three drivers, three complete tables, and two evidence-based observations satisfy the specification.
- [x] T064 Report verification results, any unverified acceptance criteria, and the local preview URL.

## Scope Guardrails

- Keep this a static semantic HTML and Tailwind CSS v4 implementation.
- Do not add application JavaScript, custom CSS, charting libraries, frontend frameworks, or a production CSS build.
- Do not add dependency manifests or persistent executable test infrastructure solely for this report.
- Do not add live integrations, authentication, databases, automatic refresh, or interactive filter/export controls.
- Do not fabricate unsupported subscription, retention, satisfaction, quality, or historical-comparison metrics.

## Execution Report

- Preview: [http://localhost:3000](http://localhost:3000), served by the unchanged existing Flask development server.
- Delivered four KPI widgets, three driver views, three operational tables, six attributed campaigns, and two evidence-backed observations.
- Sample arithmetic reconciles: EUR 4,080.00 commissions, 350 sales, 0.35% conversion, 8.90% engagement, 200.00% commission ROI, and 3.00x commission return on spend.
- Recommended HTML conformance validation passes. Editor diagnostics report no errors. The source contains only the permitted Tailwind v4 script, without custom CSS or application JavaScript.
- Chromium checks pass at 375, 640, 768, and 1280 CSS pixels. Additional integration checks cover 320, 639, and 1024 CSS pixels. No page-level horizontal overflow or clipped non-table labels was found; wide tables scroll within their own containers.
- Full-page screenshots at the four required verification widths were captured outside the repository. Mobile and desktop screenshots were visually reviewed; the local image renders and widgets do not overlap.
- Keyboard checks pass for the skip link, section navigation, visible focus, and arrow-key scrolling in all three tables.
- Automated axe WCAG A/AA checks report zero violations at 375 and 1280 CSS pixels. This is not a claim of a complete manual accessibility audit.
- 200%-equivalent reflow checks pass at effective widths of 384 and 640 CSS pixels with doubled pixel density. Native browser-menu zoom was not separately exercised; cross-browser and assistive-technology testing remain outside this verification run.
- Flask and temporary validation/browser tooling were installed in the development environment. No project dependency manifest or persistent test infrastructure was added. No live account integration is implied.