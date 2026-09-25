# Bilingual Academic Homepage Redesign

**Status:** Design for user review
**Date:** 2026-09-25

## Goal

Restructure the current single-page Jekyll academic homepage into a polished Chinese-English researcher site. The Chinese version remains at `/`; the English version lives at `/en/`. Both versions share one layout and visual system, and a visible `中 / EN` control links directly between them.

The visual direction takes cues from [pi.dev](https://pi.dev/): a quiet grid, editorial typography, small monospaced labels, fine borders, and modular content. The implementation will create its own research identity and will not reuse Pi's logo or brand assets.

## Identity and source-grounded content

- The homepage owner is **Haokun Ren**, as corrected by the user. Do not identify Ye Wang as the owner.
- Both linked arXiv records list Ye Wang first and Haokun Ren second. Preserve that author order in the publication metadata while bolding Haokun Ren as the homepage owner. Render the owner's name as “Haokun Ren” consistently.
- Describe the research using only topics supported by these papers: EEG/MEG representation learning, neural-visual alignment, and brain-to-image retrieval. Do not invent an affiliation, degree, biography, portrait, contact information, awards, talks, or other credentials.
- Include the two existing papers, with their arXiv and PDF links, publication dates, author lists, and concise Chinese and English descriptions:
  - “Adaptive Cortically Constrained EEG-Vision Alignment for Zero-Shot Brain-to-Image Retrieval” (arXiv:2609.24109).
  - “The Visual Target Matters: Learning across the Visual Hierarchy for Brain-to-Image Retrieval” (arXiv:2609.24136).
- Remove template-only News, Honors, Education, Talks, and Personal entries unless the user supplies real content for those sections.

## Information architecture

- `/` is the Chinese homepage and `/en/` is its English counterpart.
- Both pages use the same Jekyll layout and page structure, with language-specific copy, navigation labels, page titles, and descriptions.
- The language control links between the two routes without relying on JavaScript or browser storage. Use matching section anchors so navigation remains predictable in either language.
- Set the document language on each page and expose canonical and `hreflang` links for the Chinese and English versions.
- Use a compact top navigation and a single-column editorial layout. The page contains a hero/introduction, a short research section, selected publications, and a minimal footer. Omit the current sidebar because its configured avatar is missing and the profile data is placeholder text.
- Remove the global `<base target="_blank">` behavior so internal navigation and language switching stay in the same tab. External publication links may opt into a new tab individually if appropriate.

## Visual system and interaction

- Use a light paper background (`#F4F4F2`) with a subtle gray square grid (`#DEDEDA`), dark ink text (`#202020`), thin neutral rules, and cornflower blue (`#6AA6D2`) as the primary accent. Reserve coral (`#EC8E7D`) and yellow (`#EBC84D`) for the original decorative motif.
- Reuse Newsreader for the large expressive hero and Hanken Grotesk for body copy. Use the system monospace stack for uppercase section numbers and navigation labels.
- Create an original, CSS/SVG-based EEG-to-visual motif from a waveform and a small arrangement of image tiles. Keep it decorative and avoid reproducing Pi's geometric mark.
- Present publications as bordered editorial rows or cards with a clear hierarchy: date, title, owner-highlighted author list, short summary, and arXiv/PDF links.
- Make the layout responsive without horizontal overflow. Provide visible keyboard focus, semantic landmarks, adequate contrast, and reduced-motion behavior. Any animation is decorative and subtle; the language control and navigation work without JavaScript.

## Implementation boundaries

- Keep Jekyll and the current GitHub Pages branch deployment. Do not add a front-end framework or a new runtime dependency.
- Replace the theme-specific page shell with a small semantic layout and dedicated site stylesheet. Keep existing vendored theme assets in the repository but stop loading legacy theme CSS/JavaScript where the new page no longer needs them.
- Keep the two language page sources separate and explicit so both are crawlable and easy to edit. Share the shell, header/footer, and publication markup through Jekyll includes where that meaningfully reduces duplication.
- Update page metadata and SEO for both language routes. Do not change unrelated citation-crawler behavior, repository settings, or user profile fields that are not supported by known information.

## Acceptance criteria

1. `/` renders the complete Chinese page and `/en/` renders the complete English page.
2. The `中 / EN` control works from either route and points to the matching language page.
3. Each route has the correct `lang`, localized title/description, canonical URL, and alternate-language metadata.
4. The page identifies Haokun Ren as its owner without changing either paper's author order; both arXiv and PDF links are present and correct.
5. No template placeholder biography, avatar, institution, award, education, talk, or personal-interest claims remain in the rendered homepage.
6. The pi.dev-inspired grid and editorial typography remain legible on desktop and mobile; keyboard focus and reduced-motion preferences are handled.
7. A Jekyll build succeeds. After the user-approved implementation is pushed to `master`, the published homepage is checked at `https://j4ck1e2000.github.io/` and `/en/` for the updated content.

## Deployment

The user requested deployment as part of this task. Once implementation is complete and verified, commit only the site redesign files, push to the existing `master` branch, and verify the published Chinese and English pages. Report any local-build or hosting limitation with the observed evidence.
