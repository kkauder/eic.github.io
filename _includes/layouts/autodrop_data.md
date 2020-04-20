{% assign menus = site.data.menus | where: "name", "eic" %}
{% assign the_menu=menus[0] %}
<li class="nav-item dropdown px-4">
<a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="color: #fff;">{{ the_menu.full }}</a>
<div class="dropdown-menu" aria-labelledby="navbarDropdown">

{% for submenu in the_menu.submenus %}

{% assign theLink=submenu.link %}
{% assign target=site.blank %}
{% if submenu.div %}<div class="dropdown-divider"></div>{% endif %}

<a class="dropdown-item" href="{{ theLink }}" {{ target }}>{{ submenu.full }}</a>

{% endfor %}

</div>
</li>

