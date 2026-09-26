# Haokun Ren Academic Homepage

A bilingual Jekyll academic homepage published with GitHub Pages.

| Language | Route |
| --- | --- |
| Chinese | `/` |
| English | `/en/` |

## Content

- Edit the Chinese and English research sections in `_pages/about.md` and `_pages/en.md`.
- Keep localized navigation labels in `_data/navigation.yml`.
- Maintain publication titles, author order, summaries, and arXiv/PDF links in `_data/publications.yml`.
- The profile name and localized research summary live in `_config.yml` under `author`.

## Local development

```bash
bundle install
bash run_server.sh
bundle exec jekyll build
```

The site has no automated test suite. Verify changes by building the site and inspecting `_site/index.html` and `_site/en/index.html`.

## Deployment and Scholar utility

Pushing changes to `master` triggers the existing GitHub Pages deployment. The `google_scholar_crawler/` directory is a separate utility; this homepage does not load citation counts and no citation-update workflow is configured.
