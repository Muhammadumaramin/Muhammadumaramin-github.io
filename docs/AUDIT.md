# Portfolio audit and proposed corrections

Review date: November 1, 2026 (America/Chicago).
Repository: `Muhammadumaramin/Muhammadumaramin-github.io`.
Baseline commit: `4f0f722ba45c9378d882add0b88bced7f7f43f5b`.
Proposed branch: `portfolio/modernize-review`. No merge, repository rename, or hosting change is included.

## Findings and resolution

| Original issue | Proposed resolution |
| --- | --- |
| “My works” and more-projects buttons led to another GitHub user | Use Muhammadumaramin’s profile and three verified repositories |
| Market basket and Fibonacci cards linked to unrelated projects by another person | Remove these misattributed cards; retain only owned, verified project destinations |
| Instagram icon pointed to another person | Remove unverified social accounts; retain GitHub and the user-provided LinkedIn URL |
| Displayed email and phone differed from actual destinations | Set `mailto:mamin14@lamar.edu` and `tel:+14093335341` |
| CV links were `#` / `resumelink` placeholders | Provide a real printable resume page with a browser Save as PDF action |
| Student status, teaching dates, current role, and Beaumont location were stale | Add current Haifa role, ELAN and Storied Data; close GTA dates; use San Antonio and completed December 2025 degree |
| Arbitrary percentage skills and inflated template counters | Replace with factual capability groups; remove unsupported achievement/student/coffee counters |
| Paragraph/list nesting and unmatched spans | Replace entry-page markup with semantic headings, lists, sections, and landmarks |
| AOS/Waypoints and loader dependencies could hide content after a script failure | Render all content in static HTML; JavaScript only enhances menu, year, and printing |
| Continuous typing/carousel/parallax | Remove unnecessary animation; respect reduced-motion preference |
| Old jQuery 3.2.1, Bootstrap 4.3.1 and multiple vendor copies | Remove all legacy libraries from the active runtime; retain source files unchanged for recovery |
| Owl stylesheet references missing `owl.video.play.png` | Old stylesheet remains archived but is no longer loaded |
| Missing SEO and accessibility details | Add page-specific titles/descriptions, canonical and Open Graph metadata, sitemap, robots, favicon, descriptive portrait alt, skip link, focus styles, and accessible menu |
| Single-page template with weak career positioning | Six static pages: home, experience, projects, about, contact, and resume |

Original `#home-section`, `#about-section`, `#project-section`, `#resume-section`, and `#contact-section` targets remain available on the home page; resume/contact lead to relevant overview/footer areas with working links to the new pages.

## Scope and inventory

The original tree has 2 HTML files, 33 CSS files, and 31 JavaScript files. All 66 are inventoried in `legacy-asset-inventory.json`, including headers, sizes, HTML asset/link references, and CSS URL references. Custom entry markup and `js/main.js` were reviewed for structure, animation, navigation, and dependency behavior. All 31 original JS files passed `node --check`; full results are in `legacy-js-syntax.json`.

Original HTML/CSS local references were checked, including the Flaticon font demonstration page; the one missing file is recorded in `legacy-missing-references.json`. Vendor files are inventoried and syntax/reference checked, not subjected to a full third-party security review. Retained unused assets may still contain template examples and vendor URLs; none are loaded by the new pages. No claim of a complete vulnerability audit is made.

## External destinations

HTTP checks and redirect results for original entry-page links and new metadata/link destinations are in `external-link-check.json`.

- The user's GitHub profile and all three displayed project repositories returned HTTP 200 and were independently confirmed through the connected GitHub API.
- The incorrect third-party profile/project links also returned 200: their defect was attribution, not availability.
- LinkedIn did not allow automated verification. Its current destination is taken from the user's supplied profile URL, not presented as independently verified.
- Email and telephone href values match their visible text; email delivery and phone availability were not tested.
- New page canonical URLs may return 404 on the production website until this branch is merged and deployed. Their corresponding local pages pass reference checks.

## GitHub Pages evidence and limits

- The current project URL returned HTTP 200 and served the original portfolio during this audit.
- `main` remained at baseline commit during source inspection; no checked-in Actions workflow existed, and the Actions runs endpoint returned zero runs. This does not by itself identify the Pages publishing mode.
- The GitHub connector rejects the `/pages` settings endpoint as unsupported. An unauthenticated request returned 404; that does not prove Pages is disabled because the public website responds successfully.
- Exact Pages source branch/folder, build mode, custom-domain state, and enforce-HTTPS toggle could not be independently read. No settings have been changed.
- Retain the existing repository name and publishing source through review. After approval, verify **Settings → Pages** and the deployment result. Do not switch publishing to the review branch.

## Validation

- `python scripts/check_portfolio.py`: six pages; 109 HTML references; local paths and fragment IDs, unique IDs, one H1 per page, image alt, metadata, placeholders, and active runtime dependencies pass.
- `node --check assets/portfolio.js`: passes. All 31 archived JS files also parse.
- Browser QA: home and project page visual review at a 1363-pixel desktop viewport; experience navigation verified; portrait loaded correctly; no horizontal overflow observed on home.
- All six pages checked in 320-, 390-, and 768-pixel iframe viewports (effective content widths 305, 375, 753 after scrollbars): no horizontal overflow; exactly one H1 each; mobile/tablet navigation visibility correct.
- Mobile menu opens, updates `aria-expanded`, closes with Escape, and returns focus to its button.
- JavaScript-disabled iframe: home content and navigation remain available.
- Browser log inspection showed extension-origin metadata errors, with no site-origin errors observed in that inspection.
- Print styling is supplied; a physical print or full print-pagination check has not been performed. Cross-browser/device testing and a full WCAG audit remain outside this validation.

## Content review

Content uses the user's known professional background and verified project ownership. Academic analyses are explicitly labeled as academic; employer work does not link to private systems or expose operational data. No new business performance percentages, testimonials, or unsupported project metrics were invented. Employment titles/dates, contact information, and degree wording should receive the user's final editorial review in the PR before merge.

## Review and rollback

Review the screenshots and changed files in the PR. The live site remains on the original branch until approval. To preview: download/checkout the review branch and serve its root with a simple static server. To roll back after a future merge, revert the merge commit rather than deleting the repository or changing Pages settings. Original assets and all prior Git commits are preserved.
