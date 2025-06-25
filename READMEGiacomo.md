# README Giacomo

_Le cose che ho cambiato nel sito e come l'ho fatto_

## Pagina [`about.md`](_pages/about.md)

Abbastanza facile: basta modificare il Markdown. I social stanno in 	[`_data/socials.yml`](_data/socials.yml)

## Pagina [`publications.md`](_pages/publications.md)

Ho ovviamente cambiato first name e last name in modo che mettesse in bold i miei in [`_config.yml`](_config.yml), poi ho ordinato le pubblicazioni modificando sempre [`_config.yml`](_config.yml):

```
  query: "@*"
  group_by: type
  sort_by: year
  order: descending
  type_order: [preprint, article, book, phdthesis]
  type_names: { preprint: Preprints }
```
Ho rimosso la barra di ricerca cancellando la riga
```
{% include bib_search.liquid %}
```
da [`_pages/publications.md`](_pages/publications.md)

## Colori e tipografia

Ho cambiato il violetto e il grigino dei temi in IBM02 e IBM05, rispettivamente, modificando [`_sass/_themes.scss`](_sass/_themes.scss):
```
:root {
  color-scheme: light;
...
  --global-theme-color: #785ef0;
  --global-hover-color: #785ef0;
...
  --global-divider-color: #785ef0;
}
```
e
```
:root {
  color-scheme: light;
...
  --global-theme-color: #ffb000;
  --global-hover-color: #ffb000;
...
  --global-divider-color: #ffb000;
}
```
Ho cambiato il bold da first name a last name nella pagina [`about.md`](_pages/about.md) modificando [`_layouts/about.liquid`](_layouts/about.liquid)
```
<div class="post">
  <header class="post-header">
    <h1 class="post-title">
      {% if site.title == 'blank' %}
        {{ site.first_name }}</span> {{ site.middle_name }}
        <span class="font-weight-bold">{{ site.last_name }}
      {% else %}
        {{ site.title }}
      {% endif %}
    </h1>
    <p class="desc">{{ page.subtitle }}</p>
  </header>
```
e nell'header modificando [`_includes/header.liquid`](_includes/header.liquid)
```
<header>
  <!-- Nav Bar -->
  <nav id="navbar" class="navbar navbar-light navbar-expand-sm {% if site.navbar_fixed %}fixed-top{% else %}sticky-top{% endif %}" role="navigation">
    <div class="container">
      {% if page.permalink != '/' %}
        <a class="navbar-brand title font-weight-lighter" href="{{ site.baseurl }}/">
          {% if site.title == 'blank' %}
            {% if site.first_name %}
                {{- site.first_name -}}
              </span>
            {% endif %}
            {% if site.middle_name %}
              {{- site.middle_name -}}
            {% endif %}
            {% if site.last_name %}
              <span class="font-weight-bold">
              {{- site.last_name -}}
            {% endif %}
          {% else %}
            {{- site.title -}}
          {% endif %}
        </a>
      {% elsif site.enable_navbar_social %}
```
## Rimuovere pagine

Ho rimosso le pagine modificando [`_config.yml`](_config.yml):
```
# Includes & excludes
include: ["_pages", "_scripts"]
exclude:
  - bin/
  - CONTRIBUTING.md
  - CUSTOMIZE.md
  - Dockerfile
  - docker-compose.yml
  - docker-compose-slim.yml
  - FAQ.md
  - Gemfile
  - Gemfile.lock
  - INSTALL.md
  - LICENSE
  - lighthouse_results/
  - package.json
  - package-lock.json
  - _pages/about_einstein.md
  - purgecss.config.js
  - README.md
  - readme_preview/
  - vendor
  - _pages/projects.md
  - _pages/repositories.md
  - _pages/blog.md
  - _pages/profiles.md
  - _pages/dropdown.md
  - _pages/news.md
  - _pages/cv.md
  - _pages/teaching.md
  - _READMEGiacomo.md
keep_files:
  - CNAME
  - .nojekyll
```
