---
layout: default
permalink: /
lang: DE
ref: index
---

# Juhu-Wir nehmen erfolgreich am Wettbewerb teil!

<figure class="center medium">
  {% include self-linked-image.html path="/images/posts/2020-11-15-Zeitplan.jpg" alt="Zeitplan" %}
</figure>

Wir sind eines der 10 Teams, die beim CanSat-Wettbewerb angenommen wurden! Am Montag dem 09.11.20 hatten wir unsere erste Online - Veranstaltung des Wettbewerbs, das Kick-Off-Meeting. In diesem Meeting haben sich die Teams vorgestellt. Außerdem wurden uns weitere Termine, Tipps für die derzeitige Situation mit dem Corona-Virus und Erklärungen zu dem Zeitplan und der Bedienungsanleitung genannt. Auch gab es die Möglichkeit Fragen an die Veranstalter zu stellen. Danach haben wir noch ein kleines Spiel gespielt, bei dem jede Gruppe zwei wahre und eine falsche Aussage über das eigene Team bereitgestellt haben. Die anderen Teilnehmer mussten dann erraten, welche Behauptungen stimmen. Unsere Aussagen waren „unser Team ist ein internationales Team mit 5 Staatsbürgerschaften“, ,„Zwei von uns haben letztes Jahr schon am Wettbewerb teilgenommen“ und „Wir haben uns vor dem Wettbewerb schon unsere eigene Sekundärmission überlegt, bis bekannt wurde, dass dieses Jahr jeder die gleiche Sekundärmission machen soll“. Und welche ist die falsche Aussage? –Na klar, die erste, ganz so international sind wir nicht ;) Den Zeitplan haben wir abgegeben und werden jetzt vor allem Recherchearbeit erledigen. Wir freuen uns auf die zukünftigen Herausforderungen!

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

<p>Wir suchen immer noch Sponsoren. Falls Sie Interesse haben, <a href="mailto:{{ site.footer-links.email }}" target="_blank">kontaktieren Sie uns einfach.</a></p>