# Website vs. StoryMap — Budget Line Item Justifications

## Website Approach — Total: 755 hrs

### Phase 1: Data Preparation \ Content Migration (296 hrs)

#### Design data architecture (CSV/Markdown) and migrate content from 2025 Bridge Guidebook PDFs — 80 hrs

Design the normalized data schema (CSV tables, metadata dictionaries, Markdown templates) that serves as the single source of truth for the website. The current prototype uses three CSV tables as a proof of concept; the final site will require additional data files as the page structure is finalized. Then manually extract crossing data from the 2025 Bridge Guidebook PDFs into these formats.

#### Update data as 2025 data becomes available — 120 hrs

Ongoing monitoring and updating of crossing data from official sources (CBP, Bureau of Transportation Statistics, ANAM, toll operators, TxDOT district offices). Includes core crossing data (toll rates, operating hours, inspection lanes) plus datasets for visualizations — crossing volumes by mode, cross-border trade by commodities, truck/rail freight statistics, pedestrian/vehicle counts, and historical trends. Covers 35 crossings across 13 ports of entry with verification against official sources.

#### QA/QC CSV and Markdown files (No duplicated data across files) — 16 hrs

Systematic validation that no data is duplicated across tables, all Bridge-ID keys are consistent, foreign key relationships are intact, and Markdown files are properly structured. Two full passes through the dataset plus resolution of discrepancies.

#### Translate website text to allow for bilingual navigation — 80 hrs

Translation of all user-facing content — navigation, buttons, error messages, homepage content, region overviews, and 35 crossing descriptions. Requires cultural and contextual adaptation for facility names, legal terminology, and geographic references. Includes initial translation, bilingual expert review, and integration into the language-switching system. The StoryMap approach does not support bilingual content.

---

### Phase 2: Core Development (240 hrs)

#### Build scripts for web page and PDF generation (automation) — 80 hrs

Build the automation system that reads CSV data and generates: 70 bridge pages (35 × 2 languages), 6 region pages (3 × 2 languages), and 70 PDF factsheets in a pixel-perfect 3-page landscape format. Covers CSV parsing, HTML template rendering, dynamic data injection, asset management, PDF generation, edge case handling, and testing across the full dataset. Future data updates only require editing CSVs and re-running the build.

#### ArcGIS Online (AGOL) map development, integration and configuration — 80 hrs

Create and style web maps in ArcGIS Online with symbology for bridges, ports of entry, highways, and inspection facilities. Configure Experience Builder applications for 3 TxDOT districts, set zoom extents for 35 crossing maps and 3 regional overviews, and configure popups. Map development is done within the AGOL platform; integration and configuration (embedding iframes, responsive sizing, scroll behavior) is done within the website code.

#### Embed interactive data visualizations (graphs, tables) — 80 hrs

Build interactive JavaScript charts and tables: crossing volumes by mode, 10-year trend charts, trade value comparisons, toll rate tables, and lane capacity visualizations. Covers chart library development, templates for each chart type, data population for all 35 crossings, responsive design, print-friendly PDF versions, and accessibility compliance.

---

### Phase 3: Design \ Style (84 hrs)

#### *TxDOT Design Implementation:*

#### Extract and replicate navigation structure, header/footer, color scheme, typography — 16 hrs

Build responsive navigation matching TxDOT's web presence: utility bar, site header with logo and search, dropdown menus by district, footer, and mobile hamburger menu. Must handle 35+ crossing pages organized by region and port of entry. IBM Plex Sans typography and TxDOT brand colors are already implemented.

#### Reference TxDOT Brand Guidelines for official colors, logos, and standards — 16 hrs

Implement TxDOT color palette, IBM Plex Sans typography, logo usage rules, and visual hierarchy. Build a CSS design system with variables enforcing brand consistency across all pages.

#### Meet TxDOT guidance for website accessibility requirements — 32 hrs

WCAG 2.1 AA compliance: semantic HTML, ARIA labels/roles on all interactive elements, keyboard navigation, focus indicators, color contrast (4.5:1 minimum), screen reader compatibility, skip links, and responsive zoom to 200%. Accessibility is built into every component from the start.

#### *Brand Alignment:*

#### Verify alignment with TxDOT brand identity — 20 hrs

Comprehensive review against TxDOT brand standards and txdot.gov, covering logo placement, color accuracy, typography, and visual consistency. Includes stakeholder presentation and implementation of adjustments.

---

### Phase 4: Testing, QA and Deployment (90 hrs)

#### Cross-browser testing, PDF verification, and performance testing — 90 hrs

**Cross-browser (~40 hrs):** Verify across Chrome, Firefox, Safari, Edge on desktop/tablet/mobile. Test layout, navigation, maps, and data visualizations across all pages and languages.

**PDF verification (~30 hrs):** Check all 70 factsheets for layout accuracy, image quality, page breaks, and data correctness. Special attention to crossings with unusual data shapes.

**Performance (~20 hrs):** Optimize page load times for CSV-driven pages and AGOL map iframes. Test caching, image optimization, and PDF generation reliability.

---

### Phase 5: Revisions \ Final Edits (45 hrs)

#### TxDOT review and feedback — (no hours allocated)

No hours allocated — TxDOT's review timeline is unknown and outside the project team's control.

#### Content adjustments and refinements — 25 hrs

Implement TxDOT-requested changes. Single-source data model means most changes only require editing CSVs/Markdown and regenerating pages. Accounts for ~2 rounds of feedback.

#### Final edits and quality assurance — 20 hrs

Final QA pass: verify all changes, check for regressions, validate links, run accessibility check, and prepare GitHub Pages deployment. Includes handoff documentation for future updates.

---

---

## StoryMap Approach — Total: 620 hrs

### Phase 1: Data Preparation \ Content Migration (180 hrs)

#### Consolidate information in spreadsheets, PPT, and PDFs into fewer files to allow for data checking — 60 hrs

Data is scattered across Excel, PowerPoint, and PDF files. Must be consolidated into reference files before updates can begin — a manual step that must be partially repeated each update cycle.

#### Update data as 2025 data becomes available — 120 hrs

Same data gathering effort as the website approach. The difference is what happens next: in the website, updated data flows automatically through the build system; in StoryMap, each update must be manually entered into every affected component.

---

### Phase 2: Core Development (200 hrs)

#### Revise StoryMap structure to accommodate additional Mexican data — 40 hrs

Restructure StoryMap sections, add information cards, and adjust navigation to incorporate Mexican authority data (ANAM, toll operators). StoryMap's built-in templates constrain layout options, often requiring workarounds.

#### Update StoryMap text, all graphics, Tableau Dashboards, information cards, and 64 PDF documents manually — 160 hrs

The most labor-intensive task. Every piece of content must be manually copied from source files into individual StoryMap components — text blocks, Tableau dashboards, information cards, and 64 separate PDF documents. At ~4–5 hours per crossing, this is time-consuming and error-prone with no automation available.

---

### Phase 3: Design \ Style (40 hrs)

#### *Limited to StoryMap platform constraints*

#### Meet accessibility requirements (currently no guidance for StoryMaps) — 40 hrs

StoryMap generates its own markup with limited accessibility customization. No published TxDOT guidance exists for StoryMap accessibility. Covers auditing against WCAG 2.1 AA, identifying platform-imposed gaps, implementing possible workarounds, and documenting unresolvable limitations.

---

### Phase 4: Testing, QA and Deployment (80 hrs)

#### Conduct rigorous QA/QC — Check data is consistent across StoryMap text, Tableau, dashboards — 80 hrs

The same data appears in narrative text, information cards, Tableau dashboards, and PDFs — each entered separately. Must systematically compare every data point across all representations for all 35 crossings and correct discrepancies. Manual entry across disconnected components requires proportionally more validation.

---

### Phase 5: Revisions \ Final Edits (120 hrs)

#### TxDOT review and feedback — (no hours allocated)

No hours allocated — TxDOT's review timeline is unknown and outside the project team's control.

#### Content adjustments and refinements — 60 hrs

Each correction must be made in the StoryMap text, information card, Tableau dashboard, and PDF — separately. The 60 hours (3× the website estimate) reflects this multiplication of effort.

#### Final edits and quality assurance — 60 hrs

Must re-verify data consistency across all components after revisions, as each manual edit can introduce new inconsistencies. Includes re-checking all 64 PDFs. The 60 hours (3× the website estimate) reflects the compounding QA burden.

---

---

## Future Update Cycle Cost Comparison

**Website — ~266 hrs/cycle:** Update CSVs (Phase 1: ~136 hrs) → re-test (Phase 4: ~90 hrs) → minor revisions (Phase 5: ~40 hrs). Build scripts auto-regenerate all pages and PDFs. Phases 2–3 not needed.

**StoryMap — ~520 hrs/cycle:** Re-consolidate data (Phase 1: ~120 hrs) → manually update all components and 64 PDFs (Phase 2: ~200 hrs) → re-test consistency (Phase 4: ~80 hrs) → extensive revisions (Phase 5: ~120 hrs). No automation — every update is manual.

**Bottom line:** The website saves ~254 hours per update cycle, recovering the 130-hour upfront premium after one update.
