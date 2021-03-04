{% if include.table.width %}
{% assign width=include.table.width %}
{% else %}
{% assign width='100%' %}
{% endif %}

<table border="1" width="{{ width }}">
  <tr>
    {% for header in include.table.headers %}
    <th width="50%">{{ site.tablepadding }}{{ header }}</th>
    {% endfor %}
  </tr>
  {% for row in include.table.rows %}
  <tr>
    {% for item in row %}
    <td width="50%">{{ site.tablepadding }}{{ item }}</td>
    {% endfor %}
  </tr>
  {% endfor %}
  
</table>
