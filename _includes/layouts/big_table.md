{% if include.width %}
{% assign width=include.width %}
{% else %}
{% assign width='100%' %}
{% endif %}

<table border="1" width="{{ width }}">
  <tr>
    {% for header in include.headers %}
    <th align="center">{{ site.tablepadding }}{{ header }}</th>
    {% endfor %}
  </tr>
  {% for row in include.rows %}
  <tr>
    {% for item in row %}
    <td align="top">{{ site.tablepadding }}{{ item }}</td>
    {% endfor %}
  </tr>
  {% endfor %}
  
</table>
