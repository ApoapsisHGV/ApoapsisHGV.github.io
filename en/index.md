---
layout: default
permalink: /en/
lang: EN
ref: index
---

# Yay-we successfully take part in the competition!

<figure class="center medium">
  {% include self-linked-image.html path="/images/posts/2020-11-15-Zeitplan.jpg" alt="Zeitplan" %}
</figure>

We are one of the 10 teams that were accepted in the CanSat competition! On Monday 09.11.20, we had our first online event of the competition, the Kick-Off-Meeting. In this meeting, the teams introduced themselves. We were also given further dates, tips for the current situation with the Corona virus and explanations about the schedule and the instruction manual. There was also the possibility to ask questions to the organizers. Afterwards we played a little game where each group provided two true and one false statement about their own team. The other participants then had to guess which statements were true. Our statements were "our team is an international team with 5 nationalities", "two of us have already participated in the competition last year" and "we were already thinking about our own secondary mission before the competition until it was announced that this year everyone should do the same secondary mission". And which is the wrong statement? -Of course, the first one, we are not that international ;) We have submitted the schedule and will now mainly do research work. We are looking forward to the future challenges!


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

  <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read more</a>
</article>
{% endif %}
{% endfor %}

<div class="page-banner side-figure">
  <figure class="medium">
    <img src="{{ site.baseurl }}/images/logo-1024x512.png" />
  </figure>
  <div>
    <p>Our mission is called <abbr title="Apoapsis is an astronomical term: It describes the furthest point of an orbit from the central mass.">Apoapsis</abbr>, with which we want to take part at the <a href="https://cansat.de" target="_blank">German CanSat competition of 2020/21</a>.</p>
    <p><strong>What is a CanSat?</strong> A mini satellite at the size of a soda can.</p><!--beverage can?-->
    <p><strong>What does our CanSat?</strong> It measures air pressure and temperature and it also detects various objects from above so that their position on the earth's surface can be seen afterwards.</p>
    <p><a href="{{ site.baseurl }}/en/about/" class="read-more">read more</a></p>
  </div>
</div>

<p>We're still looking for sponsors, if you're interested, <a href="mailto:{{ site.footer-links.email }}" target="_blank">feel free to contact us.</a></p>
