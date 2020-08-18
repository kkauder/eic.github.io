{%- assign image=site.data.gallery | where: 'name', include.name | first -%}
{%- assign path=image.path | relative_url -%}
{% if include.format=='html' %}
<img src="{{ path }}" width="{{ include.width }}"/>
{% endif %}
