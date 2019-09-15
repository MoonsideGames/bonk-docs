---
title: "GJK2D"
date: 2019-09-14T22:47:55-07:00
weight: 10
---

Bonk uses the Gilbert-Johnson-Keerthi, or GJK, algorithm to perform narrow phase collision detection. 

To accurately check a collision, you must pass two sets of shapes and transforms to the *GJK2D.TestCollision* method. Remember that a transform operates on the vertices of a shape: it moves, rotates, and scales them in 2D space.

```cs
var circleA = new Circle(2);
var transformA = new Transform2D(new Vector2(-1, -1));
var circleB = new Circle(2);
var transformB = new Transform2D(new Vector2(1, 1));

var (result, simplex) = GJK2D.TestCollision(circleA, transformA, circleB, transformB);
```

Note that this method returns two variables. The first is whether an overlap has occurred. The second is the termination simplex. You can think of the termination simplex as a key that helps you find the penetration vector with *EPA2D*. Note that if there was no collision, the value of the simplex is irrelevant. 