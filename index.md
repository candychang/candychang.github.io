---
layout: home
permalink: /
image:
  feature: accordions_1600x800.png
---
<div class="tiles">
{% for post in site.posts %}
    {% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->
