
{% assign posts=site.posts | where:"lang", page.lang %}

<div class="row">
{% for post in posts limit: 3 %}
* [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}
</div>

