---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2026-09-27
type: landing

design:
  # Default section spacing
  spacing: '6rem'

sections:
  # ── Profile: photo, name, role, affiliation, social links, bio, interests ──
  # All of the actual content for this block lives in data/authors/me.yaml
  - block: resume-biography-3
    content:
      title: About Me
      username: me
      text: ''
      headings:
        about: 'About Me'
        education: 'Education'
        interests: 'Research Interests'
    design:
      # Gradient mesh background that adapts to the selected theme colours
      background:
        gradient_mesh:
          enable: true
      # Name heading sizing to accommodate long or short names
      name:
        size: md # Options: xs, sm, md, lg (default), xl
      # Avatar customisation
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded

  # ── News: add new items at the top of the list. One line per item, newest first. ──
  - block: markdown
    id: news
    content:
      title: News
      subtitle: ''
      text: |-
        - **October 2026** — I will present our work *Second acts in scientific and creative careers* at the Conference on Complex Systems (CCS 2026).
        - **July 2026** — Our paper [*Crowding controls the scaling of bus frequency with demand*](/publications/bus-frequency-scaling/) was published in PNAS.
        - **June 2026** — I presented our work *Second acts in scientific and creative careers* at ICSSI 2026 in Boulder.
        - **June 2026** — I presented our work *Second acts in scientific and creative careers* at NetSci 2026 in Boston.
    design:
      columns: '1'

  # ── Latest publications: the 6 most recent papers, citation style ──
  - block: collection
    id: publications
    content:
      title: Latest Publications
      text: ''
      count: 6
      filters:
        folders:
          - publications
        # Only journal articles on the homepage; the thesis is listed on the Publications page
        publication_type: 'article-journal'
        exclude_featured: false
      order: desc
      # "See all" button under the list
      archive:
        enable: true
        link: /publications/
        text: See all publications
    design:
      view: citation
---
