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
## {{ example.title }} ({{ example.date }})

![{{ example.title }}]({{ example.image }})

Cases:
{% for case in example.cases %}
- {{ case }}
{% endfor %}

Tags:
{% for tag in example.tags %}
- {{ tag }}
{% endfor %}

{{ example.content | markdownify }}
{% endfor %}
