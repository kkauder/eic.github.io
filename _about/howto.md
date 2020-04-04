---
title: How-to
abbrev: howto
layout: default
level: 0
weight: 10
---
{% include title.md %}

### Overview
The following will be of interest to the collaborators interested in contributing to this
site or involved in its maintenance.

Please take a look at the <a href="https://github.com/eic/eic.github.io" target="_blank">repository</a>
to get an idea of the general organization of the data, layouts and supporing logic.
The idea is to shape the code and content in a way that is easy to navigate
and modify. The following sections explain how this is achieved.

### Navigation
Entries in the navigation bar on top are named in a manner
consistent with the names of the folders in this project, for example the "EIC" entry in the navigation
bard is a dropdown menu with the content defined in the "_eic" folder, "Software" is associated with the
folder "_software". These folders are treated as "collections" by the Jekyll framework and they need
to be declared in the main configuration file
<a href="https://github.com/eic/eic.github.io/blob/master/_config.yml" target="_blank">_config.yml</a>.

The top-level
entries (and therefore the folders) included in the bar are defined in a concise way in its
<a href="https://github.com/eic/eic.github.io/blob/master/_includes/layouts/navbar.html" target="_blank">code</a>.

The dropdown menus are populated automatically based on the content of respective folders ("collections").
This site's design assumes the following conventions:
* each folder contains a collection of Markdown-formatted ("MD") files
* in general each file will be mapped to an entry in the dropdown menu
* each MD file is expected to be equipped with the "front matter" section
* each MD file can either be the source for the page referenced from the dropdown manu, or generate a link to
an external URL if there is a "link" attribute in the "front matter" section of that file
* the ordering of items in the menu is defined by the "weight" attribute in the "front matter" section
* to include a divider right above an entry in a dropdown menu the following entry should be added
to the front matter: "*div: yes*"

### Managing Data
Jekyll is fairly flexible when it comes to storing and manipulating structured data.
The data component of the site can reside in the "front matter" section of the Markdown-formatted
files or in separate YAML (or JSON, CSV etc) data sources. The front matter approach works well
for small sites. For scalability, it is recommended to rely mostly on dedicated data files (i.e.
files in the "_data" folder).

### Development

To productively participate in the development of this site one needs to learn the
<a href="http://jekyllrb.com/">Jekyll</a> framework and perform its installation on
a development machine. This way any modification can be validated immediately since
the locally running development server provided by Jekyll will render the site
on the local host. Basic knolwede of the <a href="https://shopify.github.io/liquid/" target="_blank">
Liquid</a> template language and in particular the "filters" that are part of it is extremely helpful.
