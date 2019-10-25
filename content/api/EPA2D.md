---
title: "EPA2D"
date: 2019-09-15T11:23:43-07:00
weight: 30
---

*EPA2D* is a static class containing a single method for computing the penetration vector of two overlapping shapes.

## Methods

##### **public static Vector2 Intersect(IShape2D shapeA, Transform2D Transform2DA, IShape2D shapeB, Transform2D Transform2DB, Simplex simplex)**

Given two sets of shapes and transforms and an initial simplex, computes a penetration vector. When motion along the penetration vector is applied, the shape-transforms are guaranteed to become separated.

**Example:**

```cs
var squareA = new Rectangle(-1, -1, 1, 1);
var transformA = Transform2D.DefaultTransform;
var squareB = new Rectangle(-1, -1, 1, 1);
var transformB = new Transform2D(new Vector2(1.5f, 0));

var (result, simplex) = GJK2D.FindCollisionSimplex(squareA, transformA, squareB, transformB);

if (result)
{
    var intersection = EPA2D.Intersect(squareA, transformA, squareB, transformB, simplex);
}
```

In this example, the resulting penetration vector will be (1, 0).