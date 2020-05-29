{% case include.what %}
{% when "software" %}	{% assign theCollection=site.software %}
{% when "computing" %}	{% assign theCollection=site.computing %}
{% when "teams" %}	{% assign theCollection=site.teams %}
{% when "about" %}	{% assign theCollection=site.about %}
{% endcase %}

{% assign the_menu = site.data.menus | where: "name", include.what | first %}

<li class="nav-item dropdown px-4">
<a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="color: #fff;">{{ the_menu.full }}</a>
<div class="dropdown-menu" aria-labelledby="navbarDropdown">

{% for submenu in the_menu.submenus %}
{% if submenu.exclude %}{% continue %}{% endif %}

{% if submenu.div %}<div class="dropdown-divider"></div>{% endif %}

{% if submenu.label %}<div class="dropdown-item" style="color: #fff; background-color: #888;">{{ submenu.full }}</div>{% continue %}{% endif %}


{% if submenu.link %}
{% assign theLink=submenu.link %}
<a class="dropdown-item" href="{{ theLink }}" {{ site.blank }}>{{ submenu.full }}&nbsp;<img src="{{ site.external_icon | relative_url }}" height="12" width="12"></a>
{% else %}

{% assign item=theCollection | where: "name", submenu.name | first %}
{% assign theLink=item.url | relative_url %}

{% assign experiment=theCollection | where: "name", submenu.name | map: "url" | first | relative_url %}
<a class="dropdown-item" href="{{ theLink }}">{{ submenu.full }}</a>

{% endif %}





{% endfor %}

</div>
</li>

