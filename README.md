# Live-Project
Introduction


For the last two weeks of my time at the Tech Academy , I worked with other developers from different areas in a team to develope a full scale Web Application in Python. Working on this project was a great learning oppertunity for fixing bugs, cleaning up code, and adding requested features. There were some big changes that could have been a large time sink, but we used what we had to deliver what was needed on time. I saw how a good developer works with what they have to make a quality product. I worked on several back end stories that I am very proud of. Because much of the site had already been built, there were also a good deal of front end stories and UX improvements that needed to be completed, all of varying degrees of difficulty. Everyone on the team had a chance to work on front end and back end stories. Over the two week sprint I also had the opportunity to work on some other project management and team programming skills that I'm confident I will use again and again on future projects.

Below are descriptions of the stories I worked on, along with code snippets.


# Back End Stories

Functioning display page that lists items in the databases
```
{% extends "BakingRecipes_base.html" %}
{% load crispy_forms_tags %}

<!-- -->
{% load crispy_forms_tags %}
<!-- -->
{% block content %}
<div class="container">
  <form method="POST">
    {% csrf_token %}
    <fieldset class="form-group">
      <legend class="border-bottom mb-4">Sign Up!</legend>
      {{ form|crispy }}
    </fieldset>
    <div class="form-group py-3">
      <input class="btn btn-outline-primary" type="submit" value="Sign Up" />
    </div>
  </form>
  <div class="border-top pt-3">
    <a class="text-muted" href="#">Already have an account? Log in.</a>
  </div>
</div>
<!-- -->
{% endblock content %}


```
