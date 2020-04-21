{% case include.what %}
{% when "software" %}	{% assign theCollection=site.software %}
{% when "computing" %}	{% assign theCollection=site.computing %}
{% when "teams" %}	{% assign theCollection=site.teams %}
{% endcase %}

{% assign menus = site.data.menus | where: "name", include.what %}
{% assign the_menu=menus[0] %}
{% assign target='' %}

<li class="nav-item dropdown px-4">
<a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="color: #fff;">{{ the_menu.full }}</a>
<div class="dropdown-menu" aria-labelledby="navbarDropdown">

{% for submenu in the_menu.submenus %}

{% if submenu.link %}
{% assign theLink=submenu.link %}
{% assign target=site.blank %}

{% else %}

{% assign items=theCollection | where: "name", submenu.name %}
{% assign item=items[0] %}
{% assign theLink=item.url | relative_url %}
{{ coll }}
{% endif %}

{% if submenu.div %}<div class="dropdown-divider"></div>{% endif %}

<a class="dropdown-item" href="{{ theLink }}" {{ target }}>{{ submenu.full }}</a>

{% endfor %}

</div>
</li>

