---
layout: index
lang: en
ref: "paper review"
---

# Paper Review  

This page lists all the paper reviews.
  
{% assign papers = site.pages  
| where_exp: "item", "item.dir == page.dir"  
| where_exp: "item", "item.name != 'index.md'"  
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
