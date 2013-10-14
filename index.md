---
layout: page
title:
tagline:
---
{% include JB/setup %}



{% for post in site.posts %}
{% if post.pgroup == null %}
<div>
    [{{ post.category }}]
    {% if post.link == null %}
      <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
    {% else %}
      <a href="{{ post.link }}" target="_blank">{{ post.title }}</a>
    {% endif %}
    <span style="color: #999;">{{ post.date | date: "%Y-%m-%d" }}</span>

    {% if post.description != null %}
    <p style="padding-left: 40px; " class="_description">{{ post.description }}</p>
    {% endif %}

    {% if post.subgroup != null %}
    <p style="padding-left: 40px; " class="_subgroup">
      {% for subpost in site.posts %}
        {% if subpost.pgroup == post.subgroup %}
          {% if subpost.link == null %}
            <a href="{{ BASE_PATH }}{{ subpost.url }}">
              {% if subpost.short != null %} {{ subpost.short }}
              {% else %} {{ subpost.title }}
              {% endif %}
            </a>、
          {% else %}
            <a href="{{ subpost.link }}" target="_blank">
              {% if subpost.short != null %} {{ subpost.short }}
              {% else %} {{ subpost.title }}
              {% endif %}
            </a>、
          {% endif %}
        {% endif %}
      {% endfor %}
    </p>
    {% endif %}
</div>
{% endif %}
{% endfor %}



