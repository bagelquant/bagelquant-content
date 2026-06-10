---
layout: index
title: "Paper Reviews"
lang: en
ref: "paper review"
---

# Paper Review  

This page lists all the paper reviews.

{% assign current_dir = page.path | replace: "index.md", "" %}
{% assign papers = site.html_pages
| where_exp: "item", "item.path != page.path"
| where_exp: "item", "item.path contains current_dir"
| sort: "name"
%}

<ul>  
{% for paper in papers %}  
<li>  
<a href="{{ paper.url | relative_url }}">  
{{ paper.title | default: paper.name | remove: ".md" }}  
</a>  
</li>  
{% endfor %}  
</ul>
