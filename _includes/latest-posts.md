
{% assign posts=site.posts | where:"lang", page.lang %}

<div class="row">
{% if len(posts) > 0 %}
{% for post in posts limit: 3 %}
* [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}
{% else %}
{{ site.t[page.lang].no_posts }}
{% endif %}
</div>

