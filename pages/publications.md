---
title: Publications
permalink: /publications/
---

<center><b>Under Construction</b></center>

{% assign sorted_publications = site.data.publications | group_by: "type" %}

{% for type in sorted_publications %}
### {{ type.name }}
{% for publication in type.items %}
  - **{{ publication.title }}**  
    *Authors*: {{ publication.authors }}  
    *Venue*: {{ publication.venue }}  
    *Year*: {{ publication.year }}  
    [Link]({{ publication.link }})
{% endfor %}
{% endfor %}