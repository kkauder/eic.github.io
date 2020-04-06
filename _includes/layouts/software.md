{% include layouts/title.md %}

{% assign items=site.data.software | where: "category", include.category %}

{% assign tutorials=items | where: "type", "tutorial" %}
{% if tutorials.size>0 %}

#### Tutorials
<table width="100%">

{% for tutorial in tutorials %}
{% include layouts/software_item.md what=tutorial %}
{% endfor %}

</table>

{% endif %}
