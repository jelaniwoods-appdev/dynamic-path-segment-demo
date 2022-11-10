# Dynamic path segments

## The Limit of Static Routes

Whenever we define a route, like for `/about` in our application to display the about page...

A **static route** is a route who's job is to do the same thing every time it's visited.

A **static route** is a route that can _only_ be accessed when a user visits the route **exactly**.

If we define a route for `/about`...

```rb
get("/about", { :controller => "application", :action => "about" })
```

Then this route **can only be activated** when a person visits `www.our-app-name.com/about` .

This works great for pages with content that <u>doesn't change</u>, like a Home, Rules, or About page...

This technique also works when we get input from a user through a form submission (since **Query Strings** are optional and are allowed on any route).

On YouTube, the video you watched is determined by a Query String

> https://www.youtube.com/watch**?v=pKO9UjSeLew**

But for apps like Twitter, Spotify, or GitHub


## What are Dynamic Routes?

Dynamic route segments are dynamic routes (a.k.a. flexible path segments, url slugs, pretty urls, and others)

Defining one route that can match multiple values.

In cases where we want to define **one route** that matches `/post/1`, `/post/abc`, or `/posts/` anything


### Why do we use them

Defining routes by using predefined paths is not always enough for complex applications. 

- Support infinite route variations
- Save time defining routes
- We need a piece of information in the dynamic part 

## How to make a Dynamic Route

Instead of a **static route**, that will only be activated when a person matches exactly one route that a person can visit:

```rb
get("/rps/rock", { :controller => "moves", :action => "play_rock" })
get("/rps/paper", { :controller => "moves", :action => "play_paper" })
get("/rps/scissors", { :controller => "moves", :action => "play_scissors" })
```

By beginning a segment of a path with a colon (`:`), we make that segment dynamic. Rails will, for the purpose of routing, allow anything there; it’s like a wildcard.


Now one route can do the work for the 3 routes we defined before.

```rb
get("/rps/:move", { :controller => "moves", :action => "play" })
```


### Using `params`


## Demo

- Define route with dynamic route segment
- Visit URL
- See params
  - where can we access `params`?

