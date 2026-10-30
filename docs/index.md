---
layout: default
title: My Taiwan Internship Journey
---

{% if site.demo %}
<div class="demo-banner"><strong>Template preview</strong> — The intern name, dates, and stories below are examples. Replace these before sharing for TEEP evaluation.</div>
{% endif %}

<section class="hero">
  <div class="hero-copy">
    <div class="eyebrow">MY TAIWAN INTERNSHIP JOURNEY</div>
    <span class="pill">{{ site.intern.program | escape }}</span>
    <h1>Hi, I'm <span class="name-accent">{{ site.intern.name | escape }}</span><span class="period">.</span></h1>
    <p class="lead">{{ site.intern.summary | escape }}</p>
    <div class="hero-facts">
      <div><span>Host</span><strong>{{ site.intern.lab | escape }} · NTUT</strong></div>
      <div><span>Stay</span><strong>{{ site.intern.stay | escape }}</strong></div>
      {% if site.intern.home_university %}<div><span>From</span><strong>{{ site.intern.home_university | escape }}{% if site.intern.country %} · {{ site.intern.country | escape }}{% endif %}</strong></div>{% endif %}
      <div><span>Research focus</span><strong>{{ site.intern.focus | escape }}</strong></div>
    </div>
    <a class="primary-link" href="{{ '/meetings/' | relative_url }}">Browse regular meetings <span aria-hidden="true">&#8594;</span></a>
  </div>
  <div class="hero-visual" aria-hidden="true">
    <div class="postcard">
      <div class="postcard-top"><span>POSTCARD FROM TAIWAN</span><span>TAIPEI · NTUT</span></div>
      <img src="{{ '/assets/photos/front1.jpeg' | relative_url }}" alt="Postcard" class="postcard-bg-img">
      <div class="postcard-bottom">RESEARCH <span>✳</span> EXPLORE <span>✳</span> GROW</div>
    </div>
  </div>
</section>

<section id="journey" class="journey-section" aria-labelledby="journey-heading">
  <div class="section-intro">
    <div><span class="eyebrow">THE STORY SO FAR</span><h2 id="journey-heading">Highlight every Two Weeks</h2></div>
    <p>Some days are for experiments, some are for exploring, and some are a bit of both. Here's how it all unfolds.</p>
  </div>

  {% assign highlights = site.highlights | sort: 'date' %}
  {% if highlights.size > 0 %}
  <div class="monthly-stories">
  {% for month in highlights %}
    <article class="month-card">
      <div class="month-photo {% unless month.cover %}month-photo-fallback{% endunless %}">
        {% if month.cover %}
          <img src="{{ month.cover | relative_url }}" alt="{{ month.cover_alt | default: month.title | escape }}" loading="lazy">
        {% else %}
          <div class="photo-doodle"><div class="doodle-sun"></div><div class="doodle-land"></div><span>My Taiwan memories</span></div>
        {% endif %}
        <span class="photo-number">HIGHLIGHT {{ forloop.index }}</span>
        {% if month.demo %}<span class="sample-sticker">SAMPLE STORY</span>{% endif %}
      </div>
      <div class="month-content">
        {% assign start_date = month.date %}
        {% assign end_ts = month.date | date: '%s' | plus: 1123200 %}
        <p class="month-date">{{ start_date | date: '%b %-d' }} – {{ end_ts | date: '%b %-d, %Y' }}</p>
        <h3>{{ month.title | escape }}</h3>
        <div class="moment"><span class="moment-icon research-icon" aria-hidden="true">01</span><div><strong>In the lab</strong><p>{{ month.research | escape }}</p></div></div>
        <div class="moment"><span class="moment-icon life-icon" aria-hidden="true">02</span><div><strong>Life in Taiwan</strong><p>{{ month.taiwan | escape }}</p></div></div>
        <div class="takeaway"><span>Something I learned</span><p>{{ month.learning | escape }}</p></div>
        <div class="month-bottom">
          <div class="tag-row">{% for tag in month.tags %}<span class="tag">{{ tag | escape }}</span>{% endfor %}</div>
          <a class="story-link" href="{{ month.url | relative_url }}">Read the full story <span aria-hidden="true">&#8594;</span></a>
        </div>
      </div>
    </article>
  {% endfor %}
  </div>
  {% else %}
    <div class="empty-state"><h3>A new adventure starts here.</h3><p>Add the first file under <code>docs/_highlights/</code> to share research and Taiwan highlights.</p></div>
  {% endif %}
</section>

{% if site.intern.looking_back %}
<section class="closing-card" aria-labelledby="looking-back-heading">
  <span class="eyebrow">LOOKING BACK</span>
  <h2 id="looking-back-heading">What I'll take home</h2>
  <p>{{ site.intern.looking_back | escape }}</p>
</section>
{% endif %}
