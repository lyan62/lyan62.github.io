---
title:  "Blogs"
layout: archive
classes: wide
permalink: /blogs/
author_profile: true
comments: true
---

I blog "daily" about running/jogging/life [here](https://www.douban.com/people/160316581/notes) (in Chinese), 
so I have something to bring my memories back.


Other than that, I'm trying to keep blogs here related to my major/research.

{% for post in site.posts %}
    {% include archive-single.html%}
{% endfor %}