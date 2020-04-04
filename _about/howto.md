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
and modify.

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
The site design is assumes the following convention:
* each folder contains a collection of Markdown-formatted ("MD") files
* in general each file will be mapped to an entry in the dropdown menu
* each MD file is expected to be equipped with the "front matter" section
* the ordering of items in the menu is defined by the "weight" attribute in the "front matter" section
* to include a divider right above an entry in a dropdown menu the following entry should be added
to the front matter: "*div: yes*"

### Development

To productively participate in the development of this site one needs to learn the
<a href="http://jekyllrb.com/">Jekyll</a> framework and perform its installation on
a development machine. This way any modification can be validated immediately since
the locally running development server provided by Jekyll will render the site
on the local hots.
