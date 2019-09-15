---
title: "Transform2D"
date: 2019-09-14T23:30:26-07:00
weight: 20
---

To create a *Transform2D*, you must provide a *Position2D* or a *Vector2* for translation (*Vector2* is converted to *Position2D* internally), a float representing rotation in degrees, and a *Vector2* representing scale.

```cs
var transform = new Transform2D(new Position2D(4, 1), 5f, new Vector2(3, 1));
```

The following section will describe how to use an *IShape2D* in conjunction with *Transform2D* to perform collision detection.