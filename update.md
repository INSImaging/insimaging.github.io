# Website Update Guide

This document serves as a prompt/reference for future updates to the SJTU Imaging-Optimization Group website (insimaging.github.io).

## Site Overview

- Built with Jekyll (al-folio theme variant)
- Hosted on GitHub Pages
- URL: https://insimaging.github.io
- Group: Institute of Natural Sciences, Shanghai Jiao Tong University
- Research areas: mathematical imaging, medical imaging, machine learning, optimization

## Directory Structure

```
_pages/          → Main site pages (about, people, publications, research, news)
_people/         → One .md file per group member
_data/cv/        → One .yml file per member (CV/profile data)
_bibliography/   → papers.bib (all publications)
_news/           → News posts (one .md per announcement)
_research/       → Research project pages (currently empty)
_includes/       → Liquid templates (people.liquid, publications.liquid, etc.)
_sass/           → Stylesheets
assets/img/people/ → Member photos
assets/img/        → General images
```

## How to Add a New Group Member

1. Add a photo to `assets/img/people/` (JPG/JPEG/PNG, any reasonable size).

2. Create `_people/<firstname_lastname>.md`:

```markdown
---
layout: cvpage
title: Full Name
img: photo_filename.jpg
cv: firstname_lastname
toc:
  sidebar: right
importance: 1
category: PhD student
webpage: true
scholar:
github:
---

Short bio paragraph here.
```

- `category`: one of `Faculty`, `Post-doc`, `PhD student`, `Master student`, `Undergraduate`, `Alumni`
- `importance`: controls sort order within category (lower = first)
- For faculty with external homepages, add `redirect: https://...` and keep `webpage: true`
- `scholar` / `github`: full URLs if available, leave blank otherwise

3. Create `_data/cv/<firstname_lastname>.yml`:

```yaml
- title: General Information
  type: map
  contents:
    - name: Email Address
      value: name at sjtu dot edu dot cn
    - name: Address
      value: Room XXX, No.6 Science Building
    - name: Research Interests
      value: Topic 1, topic 2, topic 3.
```

Optional sections (type can be `map`, `time_table`, `publications`, or `list`):

```yaml
- title: Education
  type: time_table
  contents:
    - title: PhD in Mathematics
      institution: Shanghai Jiao Tong University
      year: 2023.09 - PRESENT

- title: Selected Publications
  type: publications
  contents:
    - year: 2024.01
      name: Paper Title
      publisher: Journal Name
      authors: Author 1, Author 2
      url: https://link-to-paper

- title: Honors and Awards
  type: time_table
  contents:
    - year: 2024
      items:
        - Award name
```

## How to Add a Publication

Edit `_bibliography/papers.bib`. Each entry follows this format:

```bibtex
@article{authorYEARkeyword,
  title={Paper Title},
  author={Last1, First1 and Last2, First2 and Last3, First3},
  journal={Journal Name},
  year={2024},
  abbr={Journal},
  bibtex_show={true},
  html={https://link-to-paper},
  abstract={Abstract text here.},
  cate_primary={optimization},
  cate_secondary={imaging},
  selected={true},
}
```

In addition to the standard BibTeX fields (`title`, `author`, `journal` /
`booktitle`, `year`, `volume`, `number`, `pages`, etc.), the following custom
properties **must** be filled in for every new entry:

1. **`abbr`** — display badge for the entry. Choose exactly one of:
   - `Journal` — for journal articles
   - `Conference` — for conference / workshop papers (use with `@inproceedings`)
   - `Preprint` — for arXiv preprints and other unpublished manuscripts

2. **`bibtex_show`** — controls whether the BibTeX expand button is shown.
   Default to `true` for all entries.

3. **`abstract`** — the paper's abstract. If the user does not provide one when
   adding the paper, leave the `abstract` field empty (or omit it) and note in
   the response that the abstract should be filled in manually. Do **not**
   search the web for abstracts.

4. **`cate_primary`** and **`cate_secondary`** — topic categorization. The only
   allowed keywords are:
   - `imaging`
   - `optimization`
   - `learning`

   `cate_primary` is **required** — pick the keyword that best matches the
   paper's main contribution. `cate_secondary` is **optional** — include it
   only when the paper meaningfully spans a second area; if unused, either
   omit the field or set it to `none`.

5. **`selected`** — controls whether the paper appears in the homepage
   "Recent Papers" section.
   - Set `selected={true}` for papers in **top-tier** journals or conferences
     (e.g., SIAM journals, IEEE journals, JMLR, NeurIPS, ICML, ICLR, CVPR, ICCV,
     ECCV, AAAI, etc.)
   - Set `selected={false}` otherwise.

Other useful fields:
- `html` — link to the paper (arXiv, publisher, DOI). Always include this.
- `pdf` — local PDF in `assets/pdf/` (optional)
- `code` — link to source code repository (optional)
- `award`, `award_name` — for award-winning papers (optional)

Organize entries chronologically by year, with comment separators between
years: `% Year 2024 ---------------------------------------------------------------`.

## How to Add a News Item

Create `_news/YYYY-MM-DD.md`:

```markdown
---
layout: post
title: Short Title
date: YYYY-MM-DD
inline: true
related_posts: false
---

News content in Markdown. Use **bold** for paper titles.
```

- `inline: true` → shows only on the front page, no separate page
- `inline: false` → gets its own page (use for longer announcements)
- The 5 most recent items appear on the homepage (configured in `_config.yml` → `announcements.limit`)

## How to Move a Member to Alumni

Edit their file in `_people/`, change:
```yaml
category: Alumni
```

Note: the personal-page link icon is automatically hidden for members in the
`Alumni` category (logic in `_includes/people.liquid`). The Google Scholar and
GitHub icons remain visible. To re-enable the personal page link for a specific
alumnus, you would need to adjust that template.

## Style Conventions

- Email addresses: use `name at sjtu dot edu dot cn` format (spam protection)
- Photos: placed in `assets/img/people/`, referenced by filename only (no path)
- Names: use real full names as titles, filenames use `firstname_lastname` convention
- Layouts: `cvpage` for members with CV data, `page` for simple redirect-only entries
- Navigation order is set via `nav_order` in page front matter
- The site uses CSS custom properties for theming (light/dark mode supported)

## Build & Deploy

```bash
bundle exec jekyll build    # build the site
bundle exec jekyll serve    # local preview at localhost:4000
```

The site auto-deploys via GitHub Pages when pushed to the `master` branch.

## Common Pitfalls

- Don't use full email addresses in any public-facing file
- Ensure every `cv:` reference in a people .md has a matching .yml in `_data/cv/`
- Photo filenames are case-sensitive (`.JPG` ≠ `.jpg`)
- The `_bibliography/papers.bib` file must start with `---\n---\n` (Jekyll front matter)
- When adding Font Awesome or Tabler icons, the font files are in `assets/webfonts/` and `assets/fonts/`
