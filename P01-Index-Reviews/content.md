---
title: "See All Reviews"
slug: index-reviews
---

You are going to define a single **resource** in this app called a `Review`.

A resource is an abstract object used to organize data, code, and other features of your app. For example, a `User` resource  can keep track of logging in and out, email and passwords, a user's birthdays. In a blog, you might have an `Article` resource that would track the titles and bodies of articles and keep track of the code for publishing and sharing them.

Resources can also be related to each other. For example, articles may have comments; a building resource might have floors, and the floors may have units; a user might have friends (like in Facebook).

All resources have actions in common that are called RESTful routes. If there was anything worth memorizing in this tutorial, this is it:

![Restful routes](assets/RESTful-routes.png)

You are going to start with the index action and then show, and then we'll look at the create, edit, update, and delete.

# Adding a `/reviews` Route

Let's make a route to `/reviews` for the index action where we can see all the reviews that we've created. Eventually this will be on our root route, but we can start making it its own separate path.

```js
// app.js

// OUR MOCK ARRAY OF PROJECTS
var reviews = [
  { title: "Great Review" },
  { title: "Next Review" }
]

// INDEX
app.get('/reviews', function (req, res) {
  res.render('reviews-index', {reviews: reviews});
})
```

Notice how we are making a mock array of reviews, and sending that in as an object into the template `{reviews: reviews}`. So the variable `reviews` will be available in our template.

# Errors are Your Friends!

If you refresh `localhost:3000` right now what do you see? Probably an error. That's ok! Errors are our friends. What does the error say?

> [info]
> Errors often tell you the next step you need to talk. In this case the error is telling you that the template does not exist. Let's make it!

Now let's add the template `views/reviews-index.handlebars`. We're going to use the Handlebars.js `{{#each}}` iterator to loop over our array of reviews and display each one's title.

```html
<h1>Reviews</h1>
{{#each reviews}}
  <h5>{{this.title}}</h5>
  <small>{{this.movieTitle}}</small>
{{/each}}
```

If you refresh `localhost:3000/reviews` now what do you see?

# Setting the Root Route - `/`

Let's update the `/reviews` route to be our root route. Just change the path from `/reviews` to `/` and delete or comment out the hello world root route we made before.

```js
// app.js

// INDEX
app.get('/', function (req, res) {
  res.render('reviews-index', {reviews: reviews});
})
```

Now navigate to `localhost:3000`.

# A Challenge

Can you make changes to your `reviews` array in `app.js` and see it reflected in your `reviews-index` template?
