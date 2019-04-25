---
layout: page
<!-- title: data is my bacon -->
---

<div class="jumbotron">
  <h1 class="display-5">Hello I'm...

<div class="container">
  <div class="name">
    <div class="left">
      <span style="position: absolute">S</span>
      <span id="name">teven</span>
    </div>

    <div class="right">
      <span style="position: absolute"> G</span>
      <span id="name2">in</span>
    </div>
  </div>
</div>

</h1>

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
          <a href = "{{ post.url }}"> Header </a>
        </div>
        <div class="card-body">
          <h4 class="card-title">{{ post.title }}</h4>
          <p class="card-text">{{ post.description }}</p>
        </div>
      </div>
      </div>
    {% endfor %}
  </div>
{% endfor %}
</div>
</center>
