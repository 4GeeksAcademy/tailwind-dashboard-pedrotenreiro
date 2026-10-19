# HTML Hello

## Dashboard Visual Asset

- Local file: [assets/creator-headphones.jpg](assets/creator-headphones.jpg).
- Source: [Unsplash photograph](https://images.unsplash.com/photo-1546435770-a3e426bf472b), used under the [Unsplash License](https://unsplash.com/license).
- Intended alternative text: "Over-ear headphones, an illustrative creator product photograph."
- This is an illustrative photograph, not a photograph of Product A, B, or C. No endorsement or brand relationship is implied.

The most basic boilerplate for any 4Geeks Academy student, start your very first website from scratch.

> There is a video tutorial on [how to use this template to create your very first website here](https://youtu.be/dfbDCMu_p-0).

# Creator Ledger

A static influencer performance report built with semantic HTML and Tailwind CSS v4. The report consolidates sample Instagram, TikTok, and YouTube campaign results for September 1-30, 2026.

## Run Locally

From the repository root:

```bash
python3 -m pip install flask
python3 server.py
```

Open [http://localhost:3000](http://localhost:3000). The existing Flask server is for local development, not production deployment. Use an available alternative port if port 3000 is occupied.

The [index.html](index.html) file is also a standalone static page. Styling requires network access to the official Tailwind v4 browser runtime:

```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
```

The browser runtime is appropriate for this educational prototype. There is no production CSS build, application JavaScript, custom stylesheet, frontend framework, dependency manifest, or persistent test framework.

## Report Contents

- Outcomes: commission income, completed sales, reach-based conversion, and engagement.
- Drivers: conversion funnel, platform performance, and product performance.
- Operations: product, platform, and campaign tables, followed by two evidence-based improvement opportunities.

The layout is mobile-first, adapting with Tailwind's `sm:`, `md:`, and `lg:` breakpoints. Native section links and keyboard-focusable table scroll regions work without application JavaScript. There are no interactive filters, exports, date pickers, live account connections, or automatic refreshes.

## Sample and Calculations

The structured source sample is embedded in the `Sample data` HTML comment in [index.html](index.html). Six campaigns cover three products and three platforms, with each product appearing on two platforms. Every sale is attributed to one campaign, every conversion is one completed, non-refunded unit, and all promotional costs are assigned directly to campaigns once.

| Product | Unit price | Commission per sale |
| --- | ---: | ---: |
| A | EUR 50.00 | EUR 7.50 |
| B | EUR 120.00 | EUR 18.00 |
| C | EUR 80.00 | EUR 12.00 |

- Sales value = completed sales multiplied by the product price.
- Commission income = sales value multiplied by 15%.
- Conversion rate = completed sales / reported reach, multiplied by 100.
- Engagement rate = available interactions / reported reach, multiplied by 100.
- Interactions include available likes, comments, shares, and saves. YouTube saves are unavailable, not measured as zero. Cross-platform engagement comparisons therefore reflect available interaction types, not identical reporting coverage.
- Commission return on spend = commission income / promotional costs, expressed as a multiple.
- Commission ROI = (commission income - promotional costs) / promotional costs, multiplied by 100.
- Funnel click/reach and sale/click rates use their explicitly named denominators, not impressions.
- Aggregate rates use summed numerators and denominators. Only display values are rounded.
- Undefined ratios are N/A when reach or the applicable cost denominator is zero. All sample campaigns have positive reach and costs.
- Reported reach is summed across campaigns and is not a deduplicated count of unique people across platforms.

The sample totals are 350 sales, EUR 27,200.00 sales value, EUR 4,080.00 commissions, EUR 1,360.00 costs, 100,000 reported reach, and 8,900 available interactions. Overall conversion is 0.35%, engagement is 8.90%, commission ROI is 200.00%, and commission return on spend is 3.00x.

No previous-period trends or unsupported subscription, retention, survey, or lead-quality metrics are fabricated.

## Visual Asset

- Local file: [assets/creator-headphones.jpg](assets/creator-headphones.jpg).
- Source: [Unsplash photograph](https://images.unsplash.com/photo-1546435770-a3e426bf472b), used under the [Unsplash License](https://unsplash.com/license).
- Alternative text: "Over-ear headphones, an illustrative creator product photograph."
- The photograph is illustrative, not a photograph of Product A, B, or C. No endorsement or brand relationship is implied.

## Project Documents

- [Requirements](specs/001-dashboard/spec.md)
- [Implementation plan](specs/001-dashboard/plan.md)
- [Sequential task checklist](specs/001-dashboard/tasks.md)

Starter template provided by [4Geeks Academy](https://4geeksacademy.com/).
