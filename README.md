# Muhammad Umar Amin · Portfolio

A minimal light, multi-page portfolio for e-commerce leadership, marketplace operations, and quantitative analytics. Plain HTML, CSS, and JavaScript; no build service or runtime packages required.

## Review

This version is proposed on `portfolio/modernize-review`. The existing `main` branch and live GitHub Pages website remain unchanged until the pull request is reviewed and merged.

- [Audit and validation](docs/AUDIT.md)
- [Desktop preview](docs/preview-desktop.jpg)
- [Experience](experience.html), [projects](projects.html), [about](about.html), [contact](contact.html), [printable resume](resume.html)

To preview locally, run `python -m http.server 8000` from the repository root and open `http://localhost:8000`. The Pages project URL also works because runtime assets and navigation use relative paths.

## Edit and validate

Page content and shared markup live in `scripts/build_portfolio.py`. Change that source, then run:

```sh
python scripts/build_portfolio.py
python scripts/check_portfolio.py
node --check assets/portfolio.js
```

Commit the generated root HTML files and sitemap along with the source change. Styling and small-screen navigation live in `assets/portfolio.css` and `assets/portfolio.js`.

`resume.html` offers the browser Print / Save as PDF action; it does not advertise a nonexistent downloadable PDF. A finalized PDF can be added later without exposing a job-specific resume accidentally.

## GitHub Pages

Keep the repository name and Pages settings unchanged during review. After approval, merge the pull request into the existing publishing branch. Verify **Settings → Pages** still uses the intended source and check the deployment before sharing the updated site. The exact configured source could not be read through the available connector; see the audit for evidence and limits.

Current public URL: https://muhammadumaramin.github.io/Muhammadumaramin-github.io/

An optional future rename to `Muhammadumaramin.github.io` can provide a shorter root URL. That migration is deliberately separate: update the `BASE` value in the generator, `robots.txt`, and external references, then regenerate the HTML and sitemap. Do not rename during this PR review.

## Original assets and licenses

The new pages, stylesheet, and JavaScript are independently implemented and do not use the original Colorlib template or vendor code. Original `css/`, `js/`, `lib/`, `fonts/`, and `scss/` files are retained unchanged for recovery and keep their existing notices and licenses. They are not loaded by the new portfolio. The original portrait is reused from `images/about-me.jpg`. Historical versions are preserved in Git.
