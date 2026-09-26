# Full AcadHomepage Framework Integration Design

## Goal

Replace the current lightweight custom Jekyll shell with the actual AcadHomepage/Minimal Mistakes component stack, using upstream AcadHomepage source at commit `2cc1577eeaf2f74dede6d016a70722dbd409ea2f`. Preserve Haokun Ren's bilingual routes, research text, two arXiv papers, SEO, redirects, and GitHub Pages deployment.

This design supersedes the lightweight custom implementation in `2026-09-26-acad-homepage-style-redesign-design.md`. The user clarified that the site should use the framework itself, not only its appearance.

## Approved Direction

Use the upstream Jekyll theme structure and components in the existing repository:

- Restore the upstream shared layout pattern: compress layout, theme head, masthead, sidebar, page article, and scripts.
- Restore the upstream Minimal Mistakes Sass entry point and theme Sass modules, plus the framework's navigation scripts and icon assets needed by the theme.
- Use the framework's author profile/sidebar for Haokun Ren and `.paper-box` for publication presentation.
- Keep the current project as the repository and preserve its GitHub Pages configuration rather than replacing it with a fresh upstream clone.

The official [AcadHomepage repository](https://github.com/RayeRen/acad-homepage.github.io/tree/2cc1577eeaf2f74dede6d016a70722dbd409ea2f) documents the Minimal Mistakes-based layout, profile/sidebar, publication boxes, SEO, Scholar crawler, and Analytics options. Its [demo](https://rayeren.github.io/acad-homepage.github.io/) contains sample material; sample identity and placeholder sections will not be copied.

## Approaches Considered

1. **Restore and adapt the upstream framework in this repository (selected).** Bring back the upstream layout/includes/Sass/runtime assets from the pinned source, then adapt the existing bilingual pages and publication data. This uses the actual framework while keeping the current content, URLs, deployment target, and repository history.
2. **Replace the project with a fresh copy of upstream and transplant the content.** This is closest to a literal fork but would overwrite current Jekyll configuration, custom SEO, project documentation, and deployment assumptions, creating more migration risk.
3. **Keep the custom layout and add more upstream styling.** This would retain the one-off component system that the user asked to remove, so it does not meet the request.

## Page Structure and Localization

- Keep `/` as Chinese and `/en/` as English; keep the current page titles, descriptions, canonical URLs, and `hreflang` output.
- Use the AcadHomepage masthead and sidebar in both locales. Parameterize the root layout's document language using `page.lang` rather than the upstream demo's fixed English value.
- Keep localized navigation labels in `_data/navigation.yml`; links target the shared `research` and `publications` anchors. Keep a direct language-switch link that works without JavaScript.
- Adapt the author-profile include to read the localized bio from `site.author.bio[page.locale]`. If there is no verified portrait, render a typographic initials mark instead of a broken image or a stock/template avatar. Render no empty location, affiliation, email, or social rows.
- Keep only the verified Research and Publications sections. Do not add News, Awards, Education, Talks, or Internships without Haokun Ren's information.

## Publication Rendering and Data

- `_data/publications.yml` remains the source of publication IDs, titles, author order, owner emphasis, dates, bilingual summaries, and arXiv/PDF links.
- Adapt `_includes/publication.html` to the upstream `.paper-box` structure and theme classes while rendering the fields from that YAML data.
- Render no conference/venue badge or thumbnail unless supported by actual publication metadata and an existing image. The current papers render as text-first paper boxes with title, authors, summary, arXiv identifier, and links.
- Preserve the original author sequence and both current arXiv records exactly.

## Framework Assets and Optional Integrations

- Restore the upstream Minimal Mistakes `assets/css/main.scss`, `_sass/` modules, and the navigation/runtime/icon assets needed by its includes. Remove the current custom `assets/css/site.scss` and its bespoke header/profile/footer includes so the page has one active theme implementation.
- Retain accessibility improvements required by the current site: skip-to-content link, visible keyboard focus, responsive navigation, and a conditional author image/fallback.
- Keep the upstream license and attribution notices. Update `README.md` and `AGENTS.md` to describe the adopted AcadHomepage/Minimal Mistakes stack and the bilingual project-specific content.
- Keep the Scholar crawler source. The Scholar display and Google Analytics integrations remain disabled unless their respective IDs/data sources are configured; do not add a citation-update GitHub workflow without the user's Scholar ID and required secret. The homepage must not display template counts or failed/empty widgets.
- Preserve local favicon assets and use valid paths from the selected layout.

## Boundaries and Risks

- No author affiliation, contact information, portrait, awards, or sample template content is introduced.
- No hosting-provider or public URL change is included.
- Restoring the original framework increases the amount of vendored Sass/JS/font code compared with the custom layout; this is accepted to meet the explicit request to use the framework.
- Optional Scholar and Analytics features stay off because no corresponding author IDs are configured.

## Verification and Deployment

- Build the site with the existing Jekyll/GitHub Pages toolchain.
- Inspect `/` and `/en/` for localized language attributes, profile content, navigation destinations, canonical/hreflang tags, section IDs, both complete paper boxes, exact author order, and valid paper links.
- Inspect desktop and narrow mobile layout, navigation, profile fallback, keyboard focus, and long publication-title wrapping.
- Verify `/about/` redirects, sitemap/feed output, favicon/icon URLs, and that optional analytics/Scholar integrations emit no requests or placeholder values while unconfigured.
- Run `git diff --check`, review restored files and license attribution, push the reviewed fast-forward changes to `origin master`, and verify both deployed routes return the correct localized content.
