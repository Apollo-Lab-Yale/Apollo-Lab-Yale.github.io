---
title: Publications
permalink: /publications/
---

<a href="https://apollo-lab-yale.github.io/publications/#conference"> Conference Papers </a>

<a href="https://apollo-lab-yale.github.io/publications/#journal"> Journal Papers </a>

<hr>

{% assign sorted_publications = site.data.publications | group_by: "type" %}

{% for type in sorted_publications %}
## {{ type.name }}
{% for publication in type.items %}
  <h6 id="{{ publication.title | slugify }}">{{ publication.title }}</h6>
  **Authors**: {{ publication.authors }}  
  **Venue**: {{ publication.venue }}  
  **Year**: {{ publication.year }}  
  <a href="{{ publication.link }}" target="_blank" style="display: inline-block; vertical-align: middle;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/8/87/PDF_file_icon.svg" alt="PDF" width="20" height="20" style="vertical-align: middle;" />
  </a>
  {% if publication.video %}
  <iframe width="374" height="210" src="{{ publication.video }}" frameborder="0" allowfullscreen></iframe>
  {% endif %}
  <hr>
{% endfor %}
{% endfor %}

