
{% assign posts=site.posts | where:"lang", page.lang %}

<div class="row">
{% for post in posts %}
<div class="excerpt_post">
### [{{ post.title }}]({{ post.url | relative_url }})

{% if post.snippet-image %}
  [![Post cover image]({{ post.snippet-image | relative_url }}){:class="excerpt_cover"}]({{ post.url | relative_url }})  
{% else %}
  [![Post cover image]({{ post.cover | relative_url }}){:class="excerpt_cover"}]({{ post.url | relative_url }})
{% endif %}

{{ post.content | strip_html | truncatewords: 120 }}

[read more]({{ post.url | relative_url }})
</div>
{% endfor %}
</div>

