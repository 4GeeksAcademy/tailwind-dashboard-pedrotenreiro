# Influencer Performance Dashboard Specification

## Purpose

Provide an influencer with a consolidated view of advertising outcomes across Instagram, TikTok, and YouTube. The dashboard must answer:

- How much commission income was generated?
- Which products generated the most sales value and commission income?
- How well did promotions convert relative to reach?
- Which platforms generated the best commission return relative to costs?
- What was the engagement rate by platform and product?

## Scope and Constraints

- Deliver a static dashboard in the existing `index.html` using semantic HTML and Tailwind CSS v4 utility classes only.
- Do not introduce application JavaScript, frontend frameworks, charting libraries, other CSS frameworks, custom stylesheets, inline styles, or custom CSS rules.
- Tailwind's official v4 browser runtime is the sole permitted script: `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`. Do not use `cdn.tailwindcss.com`, Tailwind v3 configuration, or v3 setup instructions.
- The browser runtime is suitable for this educational prototype; a production CSS build is outside this scope. Initial styling requires network access to the runtime.
- Use deterministic sample data embedded in the HTML. No live integrations, database, authentication, automated imports, or backend analytics are required.
- Do not add dependency manifests or executable test infrastructure solely for this static deliverable. Any required local visual assets must be included in the repository and have meaningful alternative text where appropriate.
- Do not represent static labels as functioning filters, sorting controls, export buttons, or date pickers. Native anchor navigation is permitted.
- This specification defines requirements and acceptance criteria only. Implementation plans and task lists belong in separate documents.

## Business Rules and Metric Definitions

| Product | Unit price | Commission rate | Commission per sale |
| --- | ---: | ---: | ---: |
| Product A | EUR 50 | 15% | EUR 7.50 |
| Product B | EUR 120 | 15% | EUR 18.00 |
| Product C | EUR 80 | 15% | EUR 12.00 |

- For this sample, each conversion is one completed, non-refunded sale of one unit at the listed price.
- Sales value = conversions multiplied by the product unit price.
- Commission income = sales value multiplied by 15%.
- Conversion rate = conversions divided by reach, multiplied by 100.
- Interactions = likes + comments + shares + saves. Unsupported interaction types must be marked unavailable rather than fabricated.
- Engagement rate = interactions divided by reach, multiplied by 100. Use this denominator consistently across products and platforms.
- Commission return on spend = commission income divided by promotional costs, expressed as a multiple.
- Commission ROI = (commission income minus promotional costs) divided by promotional costs, multiplied by 100. Do not confuse this with return on spend or calculate influencer ROI from gross product sales value.
- CTR, if displayed, = clicks divided by impressions, multiplied by 100.
- Aggregate rates must be calculated from aggregate numerators and denominators, not by averaging row percentages.
- Display undefined ratios as N/A when the denominator is zero. Zero costs do not imply a zero or infinite ROI.
- Format currency consistently in euros, counts as whole numbers, and percentages consistently. Round only display values.

## Sample Data Requirements

- Include all three products, all three platforms, and at least three campaigns within one explicitly displayed reporting period.
- Each campaign sample must identify its product, platform, start and end dates, reach, impressions, clicks, interaction counts, conversions, and promotional costs.
- The sample must support both product and platform engagement rates, commission totals, conversion rates, and cost-based comparisons.
- Attribute each sale to exactly one campaign and platform so conversions and commission income are not counted twice.
- Campaigns must fall within the displayed reporting period. All KPI totals, driver summaries, rankings, and operational rows must reconcile to the same underlying sample.
- Summed reach must be labeled as reported or non-deduplicated reach, not unique people across accounts, campaigns, or platforms.
- Clearly identify the report as sample data. Do not imply that real accounts are connected or that the report refreshes automatically.
- Comparisons with a previous period are optional. If shown, provide a consistent previous-period sample and specify the comparison period.

## Information Architecture

- Provide a page header containing the dashboard identity, report title, reporting period, and sample-data status.
- Provide a labeled navigation region with native links to Outcomes, Drivers, and Operational Details. A sidebar is optional; navigation must remain usable at every viewport size.
- Use one `main` landmark and three ordered, labeled sections: top outcomes block, middle drivers block, and bottom operational details block.
- Use a single page-level heading and a logical heading hierarchy for sections and widgets.
- Reuse the same structure, spacing, typography, number formatting, and visual treatment for equivalent KPI widgets and table elements.
- Keep section layouts unframed; reserve cards for repeated widgets or individual items. Avoid nested cards.

## Top Block: Outcome KPIs

Display at least these four KPI widgets:

| KPI | Required content |
| --- | --- |
| Commission income | Total earned commission in euros; distinguish it from product sales value. |
| Completed sales | Total conversions in the reporting period. |
| Conversion rate | Completed sales divided by reported reach, expressed as a percentage. |
| Engagement rate | Total interactions divided by reported reach, expressed as a percentage. |

Each widget must contain a clear metric label, primary value, and sufficient context to interpret the value. Additional KPIs such as product sales value, commission return on spend, CTR, or cost per conversion may be included when supported by the sample.

Do not fabricate MRR, churn, retention, active users, sign-ups, NPS, CSAT, attendance, pass rates, or lead times. These require business definitions and data sources not available in this scope.

## Middle Block: Performance Drivers

Include at least these three distinct driver views:

1. **Conversion funnel:** Display reported reach, clicks, and completed sales with counts and clearly labeled stage conversion rates. Distinguish click-to-sale conversion from the reach-based overall conversion rate. Use consistent sample counts with sales no greater than clicks and clicks no greater than reported reach.
2. **Platform performance:** Compare Instagram, TikTok, and YouTube on commission income, engagement rate, conversion rate, and commission return on spend. Identify the strongest platform for each metric; do not imply one platform necessarily leads every metric.
3. **Product performance:** Compare Products A, B, and C on commission income, conversions, conversion rate, and engagement rate. Identify the highest-commission product.

An additional engagement breakdown may show likes, comments, shares, and saves. Publishing-activity summaries are optional and must use explicit sample counts when included.

Visual comparisons must use HTML and Tailwind utilities, such as labeled bars, lists, or compact tables. Do not use canvas or JavaScript charts. Exact values and labels must remain available independently of color or bar length.

## Bottom Block: Operational Details

Provide semantic tables with captions, column headers, and appropriate header scopes:

| Table | Required columns |
| --- | --- |
| Products | Product, unit price, conversions, sales value, commission income, promotional costs, commission ROI. |
| Platforms | Platform, reported reach, interactions, engagement rate, conversions, conversion rate, commission income, costs, commission return on spend. |
| Campaigns | Campaign, dates, product, platform, conversions, commission income, costs, commission ROI. |

- Product and platform rows must reconcile to campaign totals. Shared costs, if any, must have an explicit allocation rule rather than being counted more than once.
- Include at least two concise, evidence-based observations or improvement opportunities tied to the displayed data, such as a platform's high engagement but low conversion or a campaign's negative commission ROI.
- Claims of spikes, drops, or anomalies require a displayed baseline or comparison dataset. Without one, show current-period observations only.
- Rankings or top-performer lists must state their metric. Interactive filters are outside this HTML-only scope.

## Responsive and Visual Requirements

- Use a mobile-first base layout and Tailwind's `sm:`, `md:`, and `lg:` responsive variants for at least three adaptive breakpoints.
- At the smallest sizes, stack KPI widgets and driver views in a single column. Allow navigation and metadata to wrap without overlapping.
- At `sm:`, allow suitable KPI widgets to use two columns and improve navigation spacing.
- At `md:`, adapt driver views and supporting content to available tablet width while preserving readable labels.
- At `lg:`, display the four primary KPIs in one row and the three driver views side by side where practical.
- Use Tailwind spacing, sizing, and layout utilities. Do not introduce arbitrary pixel-based dimensions or custom breakpoint definitions.
- Wide tables may scroll horizontally inside their own labeled, keyboard-focusable containers. The page itself must not overflow horizontally.
- Use a restrained, coherent palette with accessible contrast and consistent positive, negative, and neutral states. Status must not rely on color alone.
- Include at least one relevant visual asset, such as an accessible product image, without making core metrics depend on its availability.
- Keep text, values, labels, and visual comparisons readable without clipping, overlaps, or viewport-scaled typography.

## Accessibility Requirements

- Set the document language and include a descriptive page title and viewport metadata.
- Provide a visible-on-focus skip link to the main content.
- Use `header`, `nav`, `main`, `section`, and `table` elements according to their meaning.
- Ensure native navigation and scrollable table containers are keyboard accessible, with visible focus indicators.
- Provide text equivalents for meaningful visual information; mark purely decorative assets appropriately.
- Meet WCAG AA text contrast expectations and preserve usability at 200% browser zoom.

## Acceptance Criteria

- The existing page renders a complete static dashboard with the three required blocks in the specified order.
- At least four KPI widgets, three driver views, three operational tables, and two data-supported observations are present.
- All three products use the specified prices and 15% commission rate; displayed totals and ratios reconcile across sections.
- Platform and product engagement rates, reach-based conversion rates, and commission-based return metrics are visible and unambiguously labeled.
- The source loads Tailwind v4 using the permitted runtime URL and contains no Tailwind v3 CDN, application scripts, custom CSS, or other styling frameworks.
- Responsive behavior is verified at approximately 375 CSS pixels (mobile), 768 (tablet), and 1280 (desktop), with an additional check around the `sm:` breakpoint. These are verification viewports, not implementation dimensions.
- At each viewport, navigation remains usable, text does not overlap, widgets adapt appropriately, and any horizontal scrolling is confined to table containers.
- Keyboard navigation, focus visibility, heading structure, table semantics, image alternatives, and 200% zoom are checked.
- The page is explicitly identifiable as a sample report and makes no unsupported claims about live data, unique cross-platform audiences, or functioning interactive controls.