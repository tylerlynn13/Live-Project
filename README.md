# Live-Project
Introduction


For the last two weeks of my time at the Tech Academy , I worked with other developers from different areas in a team to develope a full scale Web Application in Python. Working on this project was a great learning oppertunity for fixing bugs, cleaning up code, and adding requested features. There were some big changes that could have been a large time sink, but we used what we had to deliver what was needed on time. I saw how a good developer works with what they have to make a quality product. I worked on several back end stories that I am very proud of. Because much of the site had already been built, there were also a good deal of front end stories and UX improvements that needed to be completed, all of varying degrees of difficulty. Everyone on the team had a chance to work on front end and back end stories. Over the two week sprint I also had the opportunity to work on some other project management and team programming skills that I'm confident I will use again and again on future projects.

Below are descriptions of the stories I worked on, along with code snippets.


# Back End Stories

This page a Sign up form for new users or exsisting users
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

Create a recipe page, the goal of these two pages were to allow the user to create through the template rather than the admin.

```
{% extends "BakingRecipes_base.html" %}

{% block title %}Baking Recipes{% endblock %}
{% block content %}
    <h3>Recipes</h3>
    <hr>
    <div class="text-center">
        <h5>See Recipes</h5>
        <form method="POST">
            <label id="index-label">Choose Recipe:</label>
            {% csrf_token %}
            {{ form.as_p }}
            <button type="submit">Go to Recipe</button>
        </form>

    </div>
    <hr>
    <div class="text-center">
        <h5>Add another Recipe!</h5>
        <!-- Add a template to the href so the button works-->
        <button type="submit" class="new-account-button"><a href="">Create Recipe</a></button>
    </div>
{% endblock %}
```
This HTML displays the user created recipes, you have a functioning edit page for any item in the database, and the ability to delete that item.

```
{% extends 'BakingRecipes_base.html' %}

{% block content %}
    <h2>{{ recipe.title }}</h2>
    <p><strong>Description:</strong></p>
    <p>{{ recipe.description }}</p>
    <div class="buttons-container">
        <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
        <a href="{% url 'BakingRecipes_delete' recipe.id %}" class="card-link w3-button w3-black w3-round-xxlarge">Delete Recipe</a>
        <a href="{% url 'BakingRecipes_edit' recipe.id %}" class="card-link w3-button w3-black w3-round-xxlarge">Edit Recipe</a>
    </div>


{% endblock %}
```
The goal of this was to connect to the API and write a basic JSON response in the terminal

```

<h1>Search for Baking ingredients</h1>
<form action="" method="POST" style="display: inline;">
    {% csrf_token %}
    <div class="form-container">
        <input type="search" name="usr_query" placeholder="Food?, Food!, Food...">
        <button type="submit">Search for Food</button>
    </div>
</form>

```
Function for API page.

```
def bakingrecipes_api(request):
    if request.method == 'POST':
        query = request.POST.get('usr_query')

        if query == "":
            query = "chocolate"

        def textprint(obj):
            text = (json.dumps(obj, indent=4))
            return text
        endpoint = "https://world.openfoodfacts.net/api/v2/search?catagories_tags_en="
        fields = "&fields=products_name,ingredients_tags"
        print(query)
        response = requests.get(str(endpoint)+str(query)+str(fields))
        print(query)
        info = textprint(response.json())
        print(info)
        return render(request, 'BakingRecipes/BakingRecipes_api.html')
    return render(request, 'BakingRecipes/BakingRecipes_api.html')
```
# Other Skills Learned 

 * Working on a main project with a group of deveoplers, which allowed experience to see each diverse language come together in one

 * Learning how group projects efficently make and improve Web Applications

 * Practice with team programming and helping the fellow developer 
      I myself had issues with the Public API and another peer with more experience in the area was able to guide me in the direction of digging deeper into the direction I needed to       complete my API portion. I needed to get a JSON response, the given URL was JSON so we needed to dig through to find the correct URL to be able to receive back JSON.

 * Stepping out of the comfort zone and learing a lot about areas I wasn't so confortable with or were brand-new to me. 
