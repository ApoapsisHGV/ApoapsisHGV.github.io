---
layout: default
permalink: /en/
lang: EN
ref: index
---

# Christmas update 

<figure class="center medium">
  {%include self-linked.image.html path="/images/posts/2020-12-24-Designbericht.jpg" alt="Designbericht" %}
</figure>


Since we submitted the first design report for the CanSat competition on Monday 21.12.2020, we would like to give you a little update on our progress so far. We are at the end of our research phase and will soon order some components for testing. Unfortunately, we won't have much time for testing after the holidays. Due to Covid-19 the schools were closed and our exam period has been pushed back further. This means that the eleventh graders, as well as the ninth graders, will have to study for the exams directly after the holidays. But we also have good news - "knitter-switch", a local company specialising in switch technology, is sponsoring us! 

With these words, we would like to conclude this blog post and wish everyone who is reading it these days a Merry Christmas!


<p>We are still looking for sponsors. If you are interested, <a href="mailto:{{ site.footer-links.email }}" target="_blank">we would be happy if you contact us.</a></p>

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
