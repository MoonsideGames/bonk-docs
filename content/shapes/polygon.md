---
title: "Polygon"
date: 2019-09-14T20:55:54-07:00
weight: 40
---

To define a polygon, pass a variable number of **Position2D** structs representing the points of the polygon.

```cs
var polygon = new Polygon(
    new Position2D(-2, 0),
    new Position2D(0, 2),
    new Position2D(2, 0),
);
```

This polygon, for example, is a triangle.

Be careful not to define a concave Polygon, as this will cause the results of collision detection to be incorrect. Support for concave polygons is planned for a future release.

Polygons are considered equal if they define the same vertices, regardless of order. They can even be equivalent to Rectangles:

```cs
var a = new Polygon(
    new Position2D(1, 1),
    new Position2D(1, -1),
    new Position2D(-1, -1),
    new Position2D(-1, 1)
);

var b = new Rectangle(-1, -1, 1, 1);

a == b; // true!
```
