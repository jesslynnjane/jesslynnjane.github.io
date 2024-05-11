---
layout: archive
title: "Art"
permalink: /art/
---

<div class="tiles">
	{% for post in site.categories.art %}
		{% include post-grid.html %}
	{% endfor %}
</div>