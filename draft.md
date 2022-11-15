# Dynamic Routing

## The Limit of Static Routes

A **static route** is a route that can _only_ be accessed when a person visits the route **exactly**.

Meaning if we define a route for `/about` like this:

```rb
# config/routes.rb
get("/about", { :controller => "application", :action => "about" })
```

Then this route **can only be activated** when a person visits `www.our-app-name.com/about`.

This works great for pages with content that <u>doesn't change</u>, like a Home, Rules, or About page.

This technique also works well when we get input from a user through a form submission, since **Query Strings** are optional and can be added to _any_ route.

While we often use Query Strings for processing form submissions, they can be used for other app features. For example, YouTube uses a Query String to determine which video you're watching:

https://www.youtube.com/watch**?v=pKO9UjSeLew**

For other features in large apps like YouTube, the New York Times, or GitHub we _want_ routes that look like this instead:

YouTube:
- https://youtube.com/c/gorailstv
- https://youtube.com/c/google
- https://youtube.com/c/jablinskigames

New York Times:
- https://www.nytimes.com/section/todayspaper
- https://www.nytimes.com/section/politics
- https://www.nytimes.com/section/sports

GitHub
- https://github.com/raghubetina
- https://github.com/appdev-projects
- https://github.com/firstdraft

Using static routes, we would need to define very similar looking routes; one for each channel at YouTube.

```rb
get("/c/google", { :controller => "...", :action => "..." })
get("/c/gorailstv", { :controller => "...", :action => "..." })
get("/c/jablinskigames", { :controller => "...", :action => "..." })
```

Every channel on YouTube looks similar...

## What are Dynamic Routes?

Dynamic route segments are dynamic routes (a.k.a. flexible path segments, url slugs, pretty urls, and others)

Defining one route that can match multiple values.

In cases where we want to define **one route** that matches `/post/1`, `/post/abc`, or `/posts/`anything.


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

While defining a dynamic path segment in the routes with the `:` will allow the router to match _any_ route that matches the pattern, usually, the value in important and we want to use somewhere in the view template to make the UI dynamic.

Just like with query strings, we can retreive the value from the dynamic path using the name we choose in the routes.

The value is available in the `params` Hash.

So if the user is visiting `/rps/rock`, we can access `"rock"` from the `params` Hash in the controller action like this:

```rb
class MovesController < ApplicationController
  def play
    # Parameters look like:  { "move" => "rock" }
    @player_move = params.fetch("move")
    # ...
    render({ :template => "moves/play.html.erb" })
  end
end
```

## Demo

- Define route with dynamic route segment
- Visit URL
- See params
  - where can we access `params`?

<div style="overflow: hidden;padding-top: 100%;position: relative;"><iframe loading="lazy" style="border: 0;height: 100%;left: 0;position: absolute;top: 0;width: 100%;" src="https://jelani.dev/dynamic-path-segment-demo/"></iframe></div>
