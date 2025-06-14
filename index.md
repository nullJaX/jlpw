---
layout: null
---
{% assign gallery = site.gallery | sort: "title" %}{% assign gallery = gallery | sort: "date" | reverse %}

{% assign all_cases = "" | split: "" %}
{% assign all_tags = "" | split: "" %}
{% for example in gallery %}
{% assign all_cases = all_cases | concat: example.cases %}
{% assign all_tags = all_tags | concat: example.tags %}
{% endfor %}
{% assign all_cases = all_cases | uniq | sort %}
{% assign all_tags = all_tags | uniq | sort %}

**Cases**
{% for case in all_cases %}
1. {{ case }}
{% endfor %}
**Tags**
{% for case in all_tags %}
1. {{ case }}
{% endfor %}

{% for example in gallery %}
## {{ example.title }} ({{ example.date | date: "%Y/%m/%d %H:%M" }})
Cases:
{% for case in example.cases %}
- {{ case }}
{% endfor %}

Tags:
{% for tag in example.tags %}
- {{ tag }}
{% endfor %}

<img alt="{{ example.title }}" loading="lazy" src="{{ example.image }}"/>
<iframe width="300" height="200" src="{{ example.url }}" title="{{ example.title }}" loading="lazy" seamless></iframe>
{% endfor %}
