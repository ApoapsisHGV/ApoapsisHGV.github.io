---
layout: default
permalink: /
lang: DE
ref: index
---

<div class="page-banner side-figure">
  <figure class="medium">
    <img src="{{ site.baseurl }}/images/logo-1024x512.png" />
  </figure>
  <div>
    <p><abbr title="Apoapsis ist ein Begriff aus der Astronomie: Er beschreibt den Punkt, an dem ein Körper in seiner Umlaufbahn um einen Zentralkörper weitestmöglich von diesem Zentralkörper entfernt ist.">Apoapsis</abbr> heißt unsere Mission, mit der wir beim <a href="https://cansat.de">Deutschen CanSat-Wettbewerb der ESA 2019</a> teilnehmen.</p>
    <p><strong>Was ist ein CanSat?</strong> Ein Minisatellit in der Größe einer Getränkedose.</p>
    <p><strong>Was macht unser CanSat?</strong> Er misst Luftdruck und Temperatur, nimmt 3D-Fotoaufnahmen auf und stabilisiert sich dabei mit einem Reaktionsrad.</p>
    <p><a href="{{ site.baseurl }}/about/" class="read-more">mehr dazu</a></p>
  </div>
</div>

<div>
<h1>Neueste Blog-Einträge</h1>

{% assign posts=site.posts | where:"lang", page.lang %}
{% for post in posts %}
{% if post.categories contains 'cansat2019' %}
<article class="post clearfix">
  <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> <span class="meta">{{ post.date | date: "%d.%m.%Y"}}</span></h2>

  {% if post.teaserImage %}
    <figure class="left">
      <a href="{{ post.url }}">
        <img src="{{ post.teaserImage }}" alt="{{ post.title }}" />
      </a>
    </figure>
  {% endif %}

  <div class="entry">
    {{ post.excerpt }}
  </div>

  <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Weiterlesen</a>
</article>
{% endif %}
{% endfor %}
</div>
