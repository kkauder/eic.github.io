{% if include.format=="html" %}
<h4>Software Group Conveners</h4>
{% else %}
#### Software Group Conveners
{% endif %}

<table width="100%">
{% for who in site.data.people %}
{% if who.roles contains "convener" %}
<tr>
<td>{{ who.full }}</td>
<td><a href="mailto:{{ who.email }}">{{ who.email }}</a></td>
</tr>
{% endif %}
{% endfor %}
</table>

