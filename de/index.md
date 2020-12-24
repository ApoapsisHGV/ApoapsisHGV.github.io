---
layout: default
permalink: /
lang: DE
ref: index
---

# Weihnachtsupdate 

<figure class="center medium">
  {% include self-linked-image.html path="/images/posts/2020-12-24-Designbericht.jpg" alt="Zeitplan" %}
</figure>

Da wir am Montag den 21.12.2020 den ersten Designbericht für den CanSat Wettbewerb abgegeben haben, möchten wir euch ein kleines Update über unseren bisherigen Stand geben. Wir befinden uns am Ende unserer Recherchephase und werden bald einige Bauteile zum Testen bestellen. Leider werden wir nach den Ferien zunächst wenig Zeit für das Testen haben, denn aufgrund der hohen Covid-19 Fallzahlen und der damit einhergehenden Schulschließungen, wurde unsere Klausurenphase weiter nach hinten verschoben. Das heißt, auch direkt nach den Ferien müssen die Elftklässler, aber auch die Neuntklässler für die Klausuren lernen. Wir haben aber auch eine gute Neuigkeit -"knitter-switch", eine ortsansässige Firma, die sich auf Schaltertechnologie spezialisiert, sponsert uns! 

Mit diesen Worten möchten wir diesen Blogpost abschließen und wünschen Allen, die ihn heute oder in den folgenden Tagen lesen, fröhliche Weihnachten!


<p>Wir suchen noch immer Sponsoren. Falls Sie Interesse haben, würden wir uns freuen, <a href="mailto:{{ site.footer-links.email }}" target="_blank">wenn Sie uns einfach kontaktieren.</a></p>

{% assign posts=site.posts | where:"lang", page.lang %}
{% for post in posts %}
{% if post.categories contains 'cansat2020' %}
<article class="post clearfix">
  <h3><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> <span class="meta">{{ post.date | date: "%d.%m.%Y"}}</span></h3>

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

<div class="page-banner side-figure">
  <figure class="medium">
    <img src="{{ site.baseurl }}/images/logo-1024x512.png" />
  </figure>
  <div>
    <p><abbr title="Apoapsis ist ein Begriff aus der Astronomie: Er beschreibt den Punkt, an dem ein Körper in seiner Umlaufbahn um einen Zentralkörper weitestmöglich von diesem Zentralkörper entfernt ist.">Apoapsis</abbr> heißt unsere Mission, mit der wir beim <a href="https://cansat.de" target="_blank">Deutschen CanSat-Wettbewerb 2020/21</a> teilnehmen.</p>
    <p><strong>Was ist ein CanSat?</strong> Ein Minisatellit in der Größe einer Getränkedose.</p>
    <p><strong>Was macht unser CanSat?</strong> Er misst Luftdruck und Temperatur. Außerdem erkennt er verschiedene Objekte von oben, sodass hinterher ihre Position auf der Erdoberfläche erkennbar ist.</p>
    <p><a href="{{ site.baseurl }}/about/" class="read-more">mehr dazu</a></p>
  </div>
</div>

