---
layout: default
permalink: /en/
lang: EN
ref: index
---

# CanSat shipped!

<figure class="video">
  <video src="/images/posts/2021-05-20-CanSat-Innen.mp4" alt="Der CanSat von innen!" controls></video>
  <figcaption>
    The CanSat from the inside!<br />
    <a href="/images/posts/2021-05-20-CanSat-Innen.mp4">[Link to the videoo]</a>
  </figcaption>
</figure>

After many technical difficulties, we have finally finished building our CanSat and shipped it for launch. 
We are already looking forward to watching the livestream of the rocket launch and to evaluating the data recorded by our CanSat.

But how does our CanSat work?

Our CanSat has several sensors, a Raspberry Pi Zero W, a Raspberry Pi Camera Module V2 and an Arduino Nano. 

Via a temperature, air pressure and humidity sensor connected to the Arduino, measurement data is recorded. With the help of the Raspberry Pi, this data is stored on  2 USB sticks. The same applies to a NTC-Thermistor. 
The camera is directly connected to the Raspberry Pi and starts taking pictures as soon as it receives a signal sent by the Arduino. The images are stored on the USB sticks, just like the measurement data was saved.

We also have a special feature on board - a motor operated reaction wheel!

It stabilizes the CanSat during flight and prevents the rolling shutter effect.

With the help of the data of an accelerometer it is possible to find out in which "state of movement", the CanSat is currently located. This means the CanSat can determine whether the rocket launched with the CanSat or whether it is already falling.

When the CanSat lands, the buzzer is triggered and emits a loud beep, making it easier to find the CanSat.

The launch is scheduled for Tuesday, May 25 at 1 p.m., and will be streamed live at <a href="https://dlrschoollab.keymachine.eu/b/dr--e9v-hhc-g41" >https://dlrschoollab.keymachine.eu/b/dr--e9v-hhc-g41</a>.

Depending on the weather,  the launch day may be postponed to May 27 or May 31.

<figure class="center medium">
  {%include post-figure.html path="/images/posts/2021-05-20-3D-Teile.jpeg" caption="These ar the 3D-printed parts." alignement="left" image_size="medium" %}
</figure>

<figure class="center medium">
  {%include post-figure.html path="/images/posts/2021-05-20-CanSat-mit-Fallschirm.jpeg" caption="The finalized CanSat with its parachute." alignement="left" image_size="medium" %}
</figure>

<!---
<p>We are still looking for sponsors. If you are interested, <a href="mailto:{{ site.footer-links.email }}" target="_blank">we would be happy if you contact us.</a></p>
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
