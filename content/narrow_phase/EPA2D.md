---
title: "EPA2D"
date: 2019-09-14T22:54:35-07:00
weight: 20
---

If an overlap has occurred, often we wish to determine the penetration vector, which is the shortest possible vector by which one of the shapes could be moved in order for them to stop overlapping. For this purpose, Bonk implements the Expanding Polytope Algorithm.

To use this feature, you must pass the shapes and transforms as well as the simplex that is returned from the *GJK2D.TestCollision* method.

```cs
var squareA = new Rectangle(-1, -1, 1, 1);
var transformA = Transform2D.DefaultTransform;
var squareB = new Rectangle(-1, -1, 1, 1);
var transformB = new Transform2D(new Vector2(1.5f, 0));

var (result, simplex) = GJK2D.TestCollision(squareA, transformA, squareB, transformB);

if (result)
{
    var intersection = EPA2D.Intersect(squareA, transformA, squareB, transformB, simplex);
}
```

