---
title: "GJK2D"
date: 2019-09-15T11:19:13-07:00
weight: 20
---

*GJK2D* is a static class containing a single public method which is used for narrow-phase collision detection.

## Methods

##### **public static (bool, SimplexVertices) TestCollision(IShape2D shapeA, Transform2D transformA, IShape2D shapeB, Transform2D transformB)**

Returns a tuple containing two values: the collision result and the simplex. If there is an overlap, the simplex will contain the termination simplex that can be used as a starting point for the Expanding Polytope Algorithm to compute a penetration vector. Otherwise, the simplex can be ignored.

**Example:**
```cs
var circleA = new Circle(2);
var transformA = new Transform2D(new Vector2(-1, -1));
var circleB = new Circle(2);
var transformB = new Transform2D(new Vector2(1, 1));

var (result, simplex) = GJK2D.TestCollision(circleA, transformA, circleB, transformB);
```

In this example, these transformed circles are indeed overlapping, so *result* will be true and *simplex* will contain the termination simplex.