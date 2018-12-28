Github Pages

[搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)

https://jekyllcn.com/
https://github.com/mojombo/mojombo.github.io

---
layout: default
title: Tom Preston-Werner
---

    {% for post in site.posts %}
	{% for post in site.related_posts limit:3 %}
      <li><span>{{ post.date | date_to_string }}</span>{{ post.date | date_to_xmlschema }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
	
	
/_layouts/default.html
{{ page.title }}
{{ content }}

/_posts/2018-09-23-blog-title.md
{{ page.title }}

/CNAME
tom.preston-werner.com