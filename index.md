---
layout: page
<!-- title: data is my bacon -->
---

<div class="jumbotron">
<h1 class="ml5">
  <span class="text-wrapper">
    <span class="line line1"></span>
    <span class="letters letters-left">Steven</span>
    <span class="letters letters-right">Gin</span>
    <span class="line line2"></span>
  </span>
</h1>
<script>
anime.timeline({})
  .add({
    targets: '.ml5 .line',
    opacity: [0.5,1],
    scaleX: [0, 1],
    easing: "easeInOutExpo",
    duration: 700
  }).add({
    targets: '.ml5 .line',
    duration: 600,
    easing: "easeOutExpo",
    translateY: function(e, i, l) {
      var offset = -0.625 + 0.625*2*i;
      return offset + "em";
    }
  }).add({
    targets: '.ml5 .letters-left',
    opacity: [0,1],
    translateX: ["0.5em", 0],
    easing: "easeOutExpo",
    duration: 600,
    offset: '-=300'
  }).add({
    targets: '.ml5 .letters-right',
    opacity: [0,1],
    translateX: ["-0.5em", 0],
    easing: "easeOutExpo",
    duration: 600,
    offset: '-=600'
  });
  </script>

<p class="lead">Economist turned Data Scientist. Works at sfasf. Lover of all things game theory and mathematics.</p>
<hr class="my-4">
<p>This is my website where I'm learning to make web stuff and blog about my data science misadventures.</p>
<p class="lead">
  <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
</p>
</div>

<center>
<div class = "container">
{% assign rows = site.posts.size | divided_by: 2.0 | ceil %}
{% for i in (1..rows) %}
  {% assign offset = forloop.index0 | times: 2 %}
  <div class = "row">
    {% for post in site.posts limit:2 offset:offset %}
      <div class = "col-sm-6">
      <div class="card border-dark mb-3" style="max-width: 20rem;">
        <div class="card-header">
          {{ post.date | date: '%B %d, %Y' }}
        </div>
        <div class="card-body">
          <h4 class="card-title">{{ post.title }}</h4>
          <p class="card-text">{{ post.description }}</p>
          <a class="btn btn-secondary" href="{{ post.url }}" role="button">Learn more</a>
        </div>
      </div>
      </div>
    {% endfor %}
  </div>
{% endfor %}
</div>
</center>
