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

- `_pages/about.md` is the Chinese homepage and `_pages/en.md` is its English counterpart. Keep section IDs `research` and `publications` consistent.
- `_data/navigation.yml` supplies localized labels for those anchors. Keep language switching as a direct link that works without JavaScript.
- `_config.yml` stores the author's name and localized bio under `author.bio.zh` and `author.bio.en`. Do not add unverified portrait, affiliation, location, contact, social, education, award, talk, internship, or other biographical information.
- `_data/publications.yml` is the single source for publication titles, author order, dates, bilingual summaries, and arXiv/PDF links. Preserve the arXiv author order and mark Haokun Ren with `owner: true`.
- `_includes/publication-list.html` and `_includes/publication.html` render the shared publication list.

## Layout, SEO, and styling

- `_layouts/default.html` sets the page language, includes the shared navigation, profile aside, page content, and footer.
- `_includes/site-profile.html` renders the name, localized research tagline/bio, and initials mark. Do not add a placeholder image or empty profile rows.
- `_includes/seo.html` emits localized metadata, canonical URLs, and `hreflang` links.
- `assets/css/site.scss` is the active stylesheet. The desktop layout has a profile column and content column; mobile stacks them. Keep visible keyboard focus and responsive text wrapping.
- The active layout does not use a JavaScript framework. Keep the language switch and section navigation functional without JavaScript.
- `AGENTS.md` and `docs/` are excluded from the generated site in `_config.yml`.

## Legacy Google Scholar utility

`google_scholar_crawler/` is retained as a standalone utility, but the homepage has no citation-count display or configured citation-update workflow. Do not claim citations update automatically.
