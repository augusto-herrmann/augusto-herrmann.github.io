
{% assign posts=site.posts | where:"lang", page.lang %}

<div class="row">
{% unless posts == empty %}
{% for post in posts %}
<div class="excerpt_post">
### [{{ post.title }}]({{ post.url | relative_url }})

{% if post.snippet-image %}
  [![Post cover image]({{ post.snippet-image | relative_url }}){:class="excerpt_cover"}]({{ post.url | relative_url }})  
{% else %}
  [![Post cover image]({{ post.cover | relative_url }}){:class="excerpt_cover"}]({{ post.url | relative_url }})
{% endif %}

<p class="date" markdown="0">
{{ site.t[page.lang].when }}
{% if page.lang == 'en' %}
  {{ post.date | date: "%B %-d, %Y" }}
{% else %}
  {{ post.date | date: "%-d/%m/%Y" }}
{% endif %}
</p>

{{ post.content | strip_html | truncatewords: 120 }}

[{{ site.t[page.lang].read_more }}]({{ post.url | relative_url }})
</div>
{% endfor %}
{% else %}
{{ site.t[page.lang].no_posts }}
<div class="languages container">
  <ul>
  {% assign langs=site.feed.categories %}
  {% for lang in langs %}
    {% if lang != page.lang %}
      <li>
        <a href="/{{ lang }}/blog" class="btn btn-lg btn-secondary btn-{{ lang }}">{{ site.t[page.lang].languages[lang].name }}</a>
      </li>
    {% endif %}
  {% endfor %}
  </ul>
</div>
{% endunless %}
</div>

