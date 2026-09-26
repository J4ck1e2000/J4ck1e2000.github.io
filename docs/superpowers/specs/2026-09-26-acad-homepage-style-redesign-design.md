# AcadHomepage-Style Bilingual Homepage Design

## Goal

Replace the currently deployed Pi-inspired visual design with a lightweight, bilingual Jekyll implementation inspired by the layout and visual language of [AcadHomepage](https://github.com/RayeRen/acad-homepage.github.io) and its [demo](https://rayeren.github.io/acad-homepage.github.io/). Clean out site code that is no longer used by the active layout, without reintroducing the full Minimal Mistakes theme stack.

The work retains the existing `/` Chinese homepage, `/en/` English homepage, Haokun Ren identity, research description, two arXiv papers, ordered authors, publication links, localized SEO, and the already authorized GitHub Pages deployment.

## Approved Direction

Use a compact, manually maintained Jekyll layout with the visual structure of an academic homepage:

- At desktop widths, place a profile block in a narrow left column and page content in a wider right column.
- At narrow widths, stack the profile above the content without horizontal overflow.
- Use a white background, dark neutral text, blue links, restrained section rules, and ordinary readable academic typography.
- Use a compact top navigation with localized section links and a direct language switch that works without JavaScript.
- Render each publication as a simple card/row containing the existing title, ordered authors, date/arXiv identifier, bilingual summary, and arXiv/PDF links. Do not add fake thumbnails or conference badges.
- Since no verified portrait is present in the project, use a simple typographic monogram in the profile block rather than an invented portrait or unrelated image.

The homepages keep their current verified content: a short research profile and the two publications. Do not add template sections such as News, Awards, Education, Talks, or Internships until Haokun Ren supplies information for them. Do not invent an affiliation, location, email, social account, or other biography detail.

## Alternatives Considered

1. **Lightweight AcadHomepage-inspired layout (selected).** Reuse the existing bilingual data and SEO model, create the two-column academic layout with small Jekyll includes and a focused stylesheet, and remove inactive theme code. This provides the requested visual change without bringing back the legacy dependency surface.
2. **Restore the original Minimal Mistakes theme stack.** This would most closely reuse AcadHomepage's implementation, but would reactivate a large collection of legacy Sass, JavaScript, icon fonts, and theme includes. It adds complexity that is unnecessary for two static pages.
3. **Restyle the current page structure only.** This is the smallest change, but it would retain the Pi-era hero composition and would not reproduce the profile sidebar and publication-list structure that distinguish AcadHomepage.

## Page Structure and Data Flow

- `_pages/about.md` and `_pages/en.md` remain the localized content sources for `/` and `/en/`.
- `_data/navigation.yml` continues to provide localized navigation labels. The research and publications anchors remain `research` and `publications` in both languages.
- `_data/publications.yml` remains the single source for title, date, author order, Haokun Ren's author emphasis, summaries, and arXiv/PDF destinations.
- `_layouts/default.html` becomes the shared academic-page shell. It renders the localized header and footer, then a semantic `<main>` containing a profile `<aside>` and the page-content `<article>`.
- A focused `_includes/site-profile.html` renders the author's name, the current research summary, and the non-photographic monogram. The old Pi hero include is removed.
- The profile block uses only verified configuration or page data already present in the repository. The name and research summary remain visible; the current invalid portrait path and placeholder location/email are removed.
- `_includes/seo.html` continues to emit localized metadata, canonical URLs, and alternate-language links. The language switch and all navigation remain ordinary anchors.
- The page must retain the existing redirect routes and GitHub Pages URL behavior.

## Styling and Responsive Behavior

- Replace the Pi-inspired grid background, oversized hero typography, decorative brain/vision graphic, and related styling with the reference's simpler academic presentation.
- Build the profile/content columns with CSS Grid or Flexbox, with a clear breakpoint that stacks them on mobile.
- Keep visible keyboard focus, a skip-to-content link, semantic headings and navigation labels, decorative imagery hidden from assistive technology, and readable contrast.
- Preserve and correctly link the existing favicon assets from the document head.
- Do not add a front-end framework or JavaScript dependency for layout, navigation, or locale switching.

## Code Cleanup Scope

Remove files only after confirming they are not referenced by the active layout, content, build, or deployment path:

- Pi-only stylesheet rules and `images/brain-vision-mark.svg`.
- Inactive Minimal Mistakes stylesheet entry point, `_sass/` modules/vendor tree, legacy JavaScript bundles/plugins, icon font styles/fonts, and `assets/css/collapse.css`.
- Dormant theme includes: analytics, author profile, browser upgrade, Google Scholar fetch glue, custom theme head, old masthead, old scripts, old sidebar, and the old hero include.
- Dead theme configuration including the `author_profile` default, empty social/profile fields, unused analytics/verification settings, and `google_scholar_stats_use_cdn`; remove `jekyll-paginate` and `jekyll-gist` from active plugin/whitelist lists after confirming they have no site consumers, and remove exclusions that only named deleted starter assets.
- Stale template documentation that claims unsupported homepage functionality; replace it with project-specific README guidance and update `AGENTS.md` to describe the new layout and remaining standalone crawler.

Keep `google_scholar_crawler/` because it is a separate repository tool, even though this homepage has no active citation-count workflow. Keep the `site.author.name` and `site.author.bio` fields used by the profile, site URL/repository settings, `Gemfile`, Jekyll plugins that support sitemap/feed/redirect behavior, favicon files, bilingual content, publication data, SEO behavior, deployment configuration, and required license notices.

## Verification and Deployment

- Build the site with the repository's Jekyll setup.
- Inspect generated `/` and `/en/` output for localized headings, matching anchor IDs, language-switch destinations, canonical/hreflang metadata, both paper IDs, correct author order, and valid arXiv/PDF links.
- Inspect desktop and narrow mobile layouts for the two-column/stacked structure, no horizontal overflow, and visible keyboard focus.
- Run `git diff --check` and audit tracked deletions against active references, standalone crawler scope, and licenses before committing implementation changes.
- Deploy through the existing GitHub Pages branch workflow, then verify both public routes return the expected localized pages.

## Boundaries

- This work changes site layout, styling, and dead site-template code only.
- It does not alter research or publication facts, add new biography sections, rewrite the paper summaries, configure Google Scholar automation, add a portrait, or change hosting providers.
- The design is inspired by AcadHomepage's structure and visual language; it does not copy its placeholder content or require the upstream theme implementation.
