---
title: "GJK2D"
date: 2019-09-15T11:19:13-07:00
weight: 20
---

*GJK2D* is a static class containing methods for narrow-phase collision detection.

## Methods

##### **public static bool TestCollision(IShape2D shapeA, Transform2D transformA, IShape2D shapeB, Transform2D transformB)**

Tests if the two shape-transform pairs are overlapping.

**Example:**
```cs
var circleA = new Circle(2);
var transformA = new Transform2D(new Vector2(-1, -1));
var circleB = new Circle(2);
var transformB = new Transform2D(new Vector2(1, 1));

var result = GJK2D.TestCollision(circleA, transformA, circleB, transformB);
```

In this example, these transformed circles are indeed overlapping, so *result* will be true.

##### **public static (bool, Simplex) FindCollisionSimplex(IShape2D shapeA, Transform2D transformA, IShape2D shapeB, Transform2D transformB)**

Tests if the two shape-transform pairs are overlapping, and if so returns a Simplex that can be used by the EPA algorithm to determine a minimum separating vector.

**Example:**
```cs
var circleA = new Circle(2);
var transformA = new Transform2D(new Vector2(-1, -1));
var circleB = new Circle(2);
var transformB = new Transform2D(new Vector2(1, 1));

var (result, simplex) = GJK2D.TestCollision(circleA, transformA, circleB, transformB);
```

In this example, these transformed circles are indeed overlapping, so *result* will be true and *simplex* will contain the Simplex that can be used by EPA to determine a minimum separating vector.