    <h4>News</h4>
  {% assign sitedate = site.time | date: "%Y-%m-%d"   %}
  {% for post in site.news %}
    {% assign stopdate = post.until | string_to_date | date: "%Y-%m-%d" %}
    {% if stopdate > sitedate %}
<div class="row alert alert-news">
  <p class="lead event-announce">
    <a href="{{ post.url }}">
      <span class="glyphicon {{ post.symbol }}" aria-hidden="true"></span> {{ post.title }}
    </a>
  </p>
</div>
    {% endif %}
  {% endfor %}
