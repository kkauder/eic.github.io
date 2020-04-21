---
title: This Site
name: site
layout: default
level: 0
---
{% include navigation/find_link.md where=site.about what='howto' %}
{% assign howto_url=page_url %}

{% include layouts/title.md %}

#### The Goal
This website is been developed with the goal to support the software domain of the EIC community.
Its mission, technology and design principles are different for the EIC User Group website and
the Wikis used by the Working Groups to develop and share information that could change quite
often. By contrast, this portal aims to provide reliable links to the code and repositories,
curated and stable documentation and other resources necessary to advance the goals of the EIC
in the software domain.

#### The Platform
The following considerations are important for long-term viability of the site:
* ease of maintenance
* security
* performance
* portability

In order to meet these criteria this website relies on modern static
website generator technology with the following features:
* separation of the content (including text as well as numeric data and graphics) from the layout of individual pages as well as of the website as whole
* management of potentially complex structured data without reliance on databases, by keeping data in JSON, YAML and CSV formats
* flexible ways to filter, manipulate, modify and format the data to be included in the pages presented to the user
* use of a highly readable and an easy-to-edit syntax for content creation (the so-called **Markdown** syntax)

To this end, the popular <a href="http://jekyllrb.com/">*Jekyll*</a> website generator is used, with
an additional toolkit (<a href="https://getbootstrap.com/" target="_blank">*Bootstrap*</a>) for optimal user experience.
Both Jekyll and Bootstrap are free and open source.

#### Design and Implementation
To learn about the design and conventions used on this site please see the <a href="{{ howto_url }}">"How-to"</a> page.
The code is <a href="https://github.com/eic/eic.github.io">available on GitHub</a>.

#### Credits
Information collected here is managed by the <a href="http://www.eicug.org/web/content/eic-software" target="_blank" >EIC software Group</a>.
Design of this site was inspired by the <a href="http://hepsoftwarefoundation.org/">HEP Software Foundation</a> Web site.
We are grateful to the authors and maintainers of the following technologies: <a href="https://pages.github.com/">GitHub Pages</a>,
 <a href="http://jekyllrb.com/">Jekyll</a>, <a href="https://shopify.github.io/liquid/">Liquid</a>, <a href="http://getbootstrap.com/">Bootstrap</a>.

