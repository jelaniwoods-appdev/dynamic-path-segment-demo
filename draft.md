# Dynamic path segments

## What are they

Dynamic route segments are dynamic routes (a.k.a. flexible path segments, url slugs, pretty urls, and others)

Defining one route that can match multiple values.

In cases where we want to define **one route** that matches `/post/1`, `/post/abc`, or `/posts/` anything


## Why do we use them

Defining routes by using predefined paths is not always enough for complex applications. 

- Support infinite route variations
- Save time defining routes
- We need a piece of information in the dynamic part 

## How to make a dynamic route

Instead of a **static route**, that matches exactly one rouote that a person can visit:

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


## Using `params`


## Demo

- Define route with dynamic route segment
- Visit URL
- See params
  - where can we access `params`?

