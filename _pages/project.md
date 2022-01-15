---
title: "COPS IG - Projects"
layout: gridlay
excerpt: "COPS IG -- Projects."
sitemap: false
permalink: /project
---


# Projects

## Group highlights

{% assign number_printed = 0 %}
{% for publi in site.data.publist %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if publi.highlight == 1 %}

{% if even_odd == 0 %}
<hr>
<div class="row">
{% endif %}
<div>

{% if even_odd == 1 %}
<div class="col-sm-6 clearfix" style="border-left-style:solid; border-left-width: thin; border-left-color: #ccc; ">
{% else %}
<div class="col-sm-6 clearfix">
{% endif %}
  <pubtit><strong><a href="{{ site.url }}{{ site.baseurl }}{{ publi.link.url }}">{{ publi.title }}</a></strong></pubtit>
  <img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/{{ publi.image }}" class="img-responsive" width="33%" style="float: left" />
  <p>{{ publi.description }}</p>
  <p><a href="{{ publi.authorsurl }}"><em>{{ publi.authors }}</em></a></p>
  <p class="text-danger"><strong> {{ publi.news1 }}</strong></p>
</div>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endif %}
{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}
<hr>