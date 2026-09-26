# AGENTS.md

Repository guidance for coding agents working on this project.

## Project overview

This is Haokun Ren's bilingual static academic homepage, built with Jekyll and published with GitHub Pages. The Chinese page is `/`; the English page is `/en/`. Use only user-provided or cited professional information.

## Development commands

```bash
bundle install
bash run_server.sh
bundle exec jekyll build
```

There is no automated test suite or JavaScript build step. Verify changes with a Jekyll build and inspect both generated routes. `_site/` is generated output and ignored by Git. Changes to `_config.yml` require a server restart.

## Content and localization

- `_pages/about.md` and `_pages/en.md` contain the Chinese and English homepage content. Keep `page.lang`, locale-specific masthead labels, direct language switching, and shared `research`/`publications` anchors aligned.
- `_config.yml` stores `author.name` and localized `author.bio.zh` / `author.bio.en`. Do not add unverified photos, affiliations, contact details, locations, awards, talks, internships, or social profiles.
- `_data/publications.yml` is the single source for publication IDs, titles, dates, ordered authors, owner emphasis, bilingual summaries, and arXiv/PDF links.
- `_includes/publication.html` renders each record using the framework's `.paper-box` structure. Only show a venue badge or image when supported by real publication data.

## AcadHomepage / Minimal Mistakes framework

- `_layouts/default.html` provides the shared theme shell, page language, masthead, sidebar, article, and scripts.
- `_includes/masthead.html` reads `_data/navigation.yml[page.locale]`; its language switch must link directly to the alternate route.
- `_includes/sidebar.html` and `_includes/author-profile.html` use Minimal Mistakes author/profile classes. The avatar is conditional; use the initials fallback when no verified photo exists.
- `_includes/seo.html` emits localized metadata, canonical URLs, and `hreflang` links.
- `assets/css/main.scss` imports the upstream theme modules from `_sass/`; `assets/js/main.min.js`, the icon fonts, and the plugin assets support the upstream masthead/theme.
- Do not restore template placeholder sections or sample content. Keep the project license and upstream attribution notices.

## Optional integrations

Google Analytics and Scholar citation fetching are conditional and disabled without configured IDs/data. `google_scholar_crawler/` is retained separately but has no active homepage workflow. Do not claim citations update automatically.
