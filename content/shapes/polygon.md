---
title: "Polygon"
date: 2019-09-14T20:55:54-07:00
weight: 40
---

To define a polygon, pass a variable number of **Position2D** structs representing the points of the polygon.

```cs
    var polygon = new Polygon(
        new Position2D(0, 0),
        new Position2D(-1, -1),
        new Position2D(1, -1),
        new Position2D(1, 1),
        new Position2D(-1, 1)
    );
```

Be careful not to define a concave Polygon, as this will cause the results of collision detection to be incorrect.