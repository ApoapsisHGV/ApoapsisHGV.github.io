---
layout: default
permalink: /en/
lang: EN
ref: index
---

<div class="page-banner">
  <img src="{{ site.baseurl }}/images/logo-1024x512.png" />
  <div>
    <p>Our mission is called <abbr title="Apoapsis is an astronomical term: It describes the furthest point of an orbit from the central mass.">Apoapsis</abbr>, with which we want to take part at the <a href="https://cansat.de">ESA's German CanSat competition of 2019</a>.</p>
    <p><strong>What is a CanSat?</strong> A mini satellite at the size of a soda can.</p>
    <p><strong>What does our CanSat do?</strong> It measures air pressure and temperature, takes 3D pictures and stabilizies itself using a reaction wheel.</p>
    <p><a href="{{ site.baseurl }}/en/about/" class="read-more">more about this</a></p>
  </div>
</div>

<div>
<h1>Newest blog posts</h1>

{% assign posts=site.posts | where:"lang", page.lang %}
{% for post in posts %}
{% if post.categories contains 'cansat2019' %}
<article class="post clearfix">
  <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a> <span class="meta">{{ post.date | date: "%d/%b/%Y" }}</span></h2>

  {% if post.teaserImage %}
    <figure class="teaser-image">
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
</div>