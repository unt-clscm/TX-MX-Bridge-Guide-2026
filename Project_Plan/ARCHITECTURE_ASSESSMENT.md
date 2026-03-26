# Architecture Assessment: CSV-Driven Content Management

## Is this pattern common?

**The CSV-as-database + client-side rendering pattern is uncommon** for production websites, but it's not unheard of — it sits in a niche between a few more mainstream approaches.

**What's normal about it:**
- Separating content from presentation (universal best practice)
- Using markdown for long-form content (very common — Jekyll, Hugo, Gatsby, Astro all do this)
- Data-driven page generation from structured files (common in static site generators)

**What's unusual about it:**
- **CSV as the data layer** — CSVs are great for spreadsheets but lack nesting, relationships, and types. Most developers would use JSON, a database, or a headless CMS instead.
- **Client-side CSV parsing** — Fetching and parsing CSVs in the browser on every page load adds latency and fragility. The typical approach is to process data at *build time* and ship pre-rendered HTML.
- **Empty HTML shells populated by JS** — This is essentially a hand-rolled single-page app pattern without the framework. It works, but it means no content without JavaScript, poor SEO, and slower perceived load times.

## How common is each tier?

| Approach | Prevalence |
|----------|-----------|
| Headless CMS + static site generator (Contentful + Next.js, etc.) | Very common (industry standard for content sites) |
| Markdown files → build-time HTML (Hugo, Jekyll, Astro) | Very common (especially government/docs sites) |
| JSON data files + build step | Common |
| CSV → client-side rendering | Rare — mostly seen in data dashboards, not content sites |

## Why CSV-driven is rare for content sites

1. **CSVs can't represent hierarchy** — nested data (like a crossing with multiple modes, each with multiple toll tiers) requires multiple tables and joins, which is exactly what you have with 3 separate CSV files. A single JSON or YAML file handles this naturally.
2. **No build step = no safety net** — if a CSV has a formatting error (stray comma, unescaped quote), the site breaks at runtime in the user's browser rather than failing at build time where a developer can catch it.
3. **SEO and accessibility** — empty HTML shells that fill via JavaScript are invisible to search engines and screen readers until JS executes.

## How would a typical web developer approach this?

For a **35-page data-driven government site** with PDF generation needs, the most common approaches would be:

### Option A — Static site generator (most likely choice)

- Store crossing data in JSON/YAML files (one per crossing) or a single large JSON
- Use a tool like **Astro**, **Eleventy**, or **Hugo** to generate all 35 HTML pages at build time
- Markdown for long-form content (already in use)
- Output is plain HTML — fast, accessible, SEO-friendly, works without JS
- PDF generation via Puppeteer/Playwright against the built HTML

### Option B — Headless CMS (for non-technical editors)

- Store data in something like Strapi, Contentful, or even Airtable
- Pull data at build time, generate static pages
- Non-developers can edit content through a GUI

### Option C — Current approach, but with a build step

- Keep the CSVs (they're convenient for the team editing in Excel)
- Add a Node.js build script that reads the CSVs, joins them, and generates complete HTML pages
- Ship pre-rendered HTML instead of empty shells
- This aligns with the planned Node.js build system noted in project docs

## The pragmatic view

The current architecture **makes sense given the constraints**: no frameworks, a team comfortable with spreadsheets, and a prototype phase. CSVs are easy to edit in Excel, and client-side rendering lets you iterate without a build step.

**Option C is probably the natural next step** — keep CSVs as the editing format (the team already knows them), but add the planned Node.js build step to pre-render the pages. You get the best of both worlds: easy content editing *and* fast, accessible, SEO-ready output.
