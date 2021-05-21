---
layout: default
permalink: /
lang: DE
ref: index
---

# CanSat versendet!


<figure class="video medium">
  <video src="/images/posts/2021-05-20-CanSat-Innen.mp4" alt="Der CanSat von innen!" controls></video>
  <figcaption>
    Der CanSat von innen!<br />
    <a href="/images/posts/2021-05-20-CanSat-Innen.mp4">[Link zum Video]</a>
  </figcaption>
</figure>



Nach vielen technischen Schwierigkeiten haben wir nun endlich unseren CanSat fertig gebaut und für den Start verschickt. 
Wir freuen uns bereits den Livestream des Starts zu sehen und danach die Ergebnisse des CanSats auswerten zu dürfen.

Aber wie funktioniert unser CanSat?

Unser CanSat verfügt über mehrere Sensoren, einen Raspberry Pi Zero W, ein Raspberry Pi Camera Module V2 und einen Arduino Nano. 

Durch einen am Arduino angeschlossenen Temperatur-, Luftdruck- und Feuchtigkeitssensor  werden Messdaten aufgenommen. Mithilfe des  Raspberry Pis können diese auf 2 USB-Sticks gespeichert werden. Das Gleiche trifft auf einen NTC-Thermistor zu. 
Die Kamera ist direkt mit dem Raspberry Pi verbunden und nimmt auf ein Signal vom Arduino Bilder auf. Diese werden wie die Messdaten auf den USB-Sticks gespeichert.

Wir haben zudem eine Besonderheit an Bord - ein motorbetriebenes Reaktionsrad!

Dieses soll den CanSat während des Flugs stabilisieren und den Rolling-Shutter-Effekt verhindern.

Mithilfe der Daten eines Accelerometers kann in Erfahrung gebracht werden, in welcher "Phase" der CanSat sich befindet. Das heißt, es kann festgestellt werden, ob der CanSat  gestartet ist oder bereits aus der Rakete geworfen wurde und sich somit im Fall befindet.

Bei der Landung des CanSats geht dann der Buzzer an, der einen lauten Signalton von sich gibt, sodass ein Auffinden des CanSats vereinfacht wird.

Am Dienstag den 25.05 um ca. 13 Uhr soll der Start stattfinden, dieser wird live unter <a href="https://dlrschoollab.keymachine.eu/b/dr--e9v-hhc-g41">https://dlrschoollab.keymachine.eu/b/dr--e9v-hhc-g41</a>gestreamt.

Abhängig vom Wetter könne der Starttag auf den 27.05 oder 31.05 verschoben werden.

<figure class="center medium">
  {%include post-figure.html path="/images/posts/2021-05-20-3D-Teile.jpeg" caption="Das sind die 3D-gedruckten Teile." alignement="left" image_size="medium" %}
</figure>

<figure class="center medium">
  {%include post-figure.html path="/images/posts/2021-05-20-CanSat-mit-Fallschirm.jpeg" caption="Der verschlossene CanSat mit dem angehängten Fallschirm." alignement="left" image_size="medium" %}
</figure>


<!---
<p>Wir suchen noch immer Sponsoren. Falls Sie Interesse haben, würden wir uns freuen, <a href="mailto:{{ site.footer-links.email }}" target="_blank">wenn Sie uns einfach kontaktieren.</a></p>
-->

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
