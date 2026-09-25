# AGENTS.md

Repository guidance for coding agents working on this project.

## Project overview

This is a static Jekyll academic homepage for Haokun Ren, published with GitHub Pages. The Chinese page is `/`; the English page is `/en/`. Keep both versions aligned and use only user-provided or cited professional information.

## Development commands

```bash
bundle install
bash run_server.sh
bundle exec jekyll build
```

There is no automated test suite or JavaScript build step. Use a Jekyll build and inspect both generated routes when verifying site changes. `_site/` is generated output and is ignored by Git. Changes to `_config.yml` require a server restart.

## Content and localization

- `_pages/about.md` is the Chinese homepage (`permalink: /`); `_pages/en.md` is its English counterpart (`permalink: /en/`). Keep section IDs `research` and `publications` consistent across both pages.
- `_data/navigation.yml` provides localized labels for those shared anchors. Update both `zh` and `en` entries when changing the section navigation.
- `_data/publications.yml` is the single source for publication titles, ordered authors, dates, bilingual summaries, and arXiv/PDF links. Mark Haokun Ren with `owner: true`; preserve the author order from the arXiv record.
- `_includes/publication-list.html` and `_includes/publication.html` render the shared, localized publication list.
- Do not invent affiliations, degrees, contact information, awards, talks, or personal details. Remove template placeholders rather than presenting them as facts.

## Layout, SEO, and styling

- `_layouts/default.html` sets the page language and assembles the shared header, hero, page content, and footer. `_includes/site-header.html` renders localized navigation and a direct language link; language switching must work without JavaScript.
- `_includes/seo.html` emits localized title/description, canonical URLs, and `hreflang` links. `_config.yml` defines the canonical site URL and the author's supported identity metadata.
- `assets/css/site.scss` is the active site stylesheet. `assets/css/main.scss` and the Minimal Mistakes theme assets are legacy files; the new layout should not load their theme styles or JavaScript.
- `images/brain-vision-mark.svg` is a decorative, original EEG-to-visual mark. Keep it hidden from assistive technology when used as decoration.
- `AGENTS.md` is excluded from the generated site in `_config.yml`.

## Legacy Google Scholar files

The crawler and fetch include remain in the repository, but the redesigned layout does not load them and `.github/` has no citation workflow. Do not describe citation counts as automatically updating or change this legacy behavior unless asked.
