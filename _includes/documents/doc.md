{%- assign item = site.data.documents | where: "name", include.name | first -%}
{% comment %}
[{{ item.title }}]({{ item.url }}){:target="_blank"} ({{ item.author }})
{% endcomment %}
<a href="{{ item.url }}" target="_blank">{{item.title}}</a> ({{ item.author }})


