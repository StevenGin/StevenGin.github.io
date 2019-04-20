---
layout: page
<!-- title: data is my bacon -->
---
<div class="jumbotron">
  <h1 class="display-3">Hello, world!</h1>
  <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
  <hr class="my-4">
  <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
  <p class="lead">
    <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
  </p>
</div>



<!--I want to to make this into a 4 card layout of 4 most rcent projects  -->
<center>
{% for post in site.posts limit:4 %}
  <div class="card border-dark mb-3" style="max-width: 20rem;">
    <div class="card-header">
      <a href = "{{ post.url }}"> Header </a>
    </div>
    <div class="card-body">
      <h4 class="card-title">{{ post.title }}</h4>
      <p class="card-text">{{ post.description }}</p>
    </div>
  </div>
{% endfor %}
</center>
