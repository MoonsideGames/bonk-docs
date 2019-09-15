---
title: "Overview"
date: 2019-09-14T19:19:03-07:00
weight: 5
---

In Bonk, an *IShape2D* is defined by two methods.

1) A *support function*, which is a method that returns the farthest possible point in the shape in a given *Vector2* direction. The shape vertices are transformed by a *Transform2D*.

2) A method for creating an axis-aligned bounding box from the shape that takes a *Transform2D* to transform the shape vertices.

Bonk provides you with tested implementations of four common 2D shapes, but you can implement these methods to create custom *IShape2D* structs.

Note that shapes themselves do not contain absolute position data. You will use a *Transform2D* to manipulate the shape's position, rotation, and scale in 2D space.

A final restriction to note: Defining concave shapes is an error. The collision solving algorithm that Bonk uses does not support concave shapes. If you wish to define concave shapes, define them as a composition of multiple convex shapes.