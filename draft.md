# Dynamic path segments

## What are they

Dynamic route segments are dynamic routes (a.k.a. flexible path segments, url slugs, pretty urls, and others)

Defining one route that can match multiple values.

## Why do we use them

- Support infinite route variations
- Save time defining routes

## How to define

By beginning a segment of a path with a colon (`:`), we’re making it dynamic. Rails will, for the purpose of routing, allow anything there; it’s like a wildcard.

## Demo

- Define route with dynamic route segment
- Visit URL
- See params
  - where can we access `params`?

