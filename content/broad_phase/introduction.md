---
title: "Introduction"
date: 2019-09-14T18:36:07-07:00
---

Let's say we have a room with 100 objects. How do we know if any of those 100 objects are touching one another?

The naive solution is to simply check each pair of objects and see if they are colliding.

Unfortunately, this will require 10000 comparisons.

In other words, this naive approach becomes *extremely* expensive as the number of collision objects grows.

The solution? Broad-phase collision detection.

The purpose of the broad-phase is to very quickly check if an object *might* be touching another object. Then, once we know that an object might be touching another object, we can do a more expensive and accurate test.

There are a few different ways to do this. The only way that Bonk currently implements is the *spatial hash* technique.