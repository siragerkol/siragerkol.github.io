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

  # ── News: the items live in data/news.yaml (add new ones at the top of that file). ──
  # The homepage shows the 10 most recent, with a link to the full list on /news/ once there are more.
  - block: markdown
    id: news
    content:
      title: News
      subtitle: ''
      text: '{{< news limit=10 >}}'
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
