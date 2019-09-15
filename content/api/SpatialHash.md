---
title: "SpatialHash<T>"
date: 2019-09-15T11:28:40-07:00
weight: 10
---

*SpatialHash<T>* is used for broad-phase collision detection. It can quickly return a set of potential collisions of a transformed shape. *SpatialHash<T>* takes an ID type that is used to avoid comparing certain shape-transforms.

## Methods

##### **public SpatialHash(int cellSize)**

Constructor method. Takes an integer representing the width of a cell in the spatial hash.

The cell width must not be too large or too small. If the cell width is too small, then shape-transforms will occupy many cells, and the hash check will have to check all of those cells for potential collisions. If the cell width is too large, then many shape-transforms will be contained in each cell and many expensive collision tests will have to be made.

A good rule of thumb is picking a cell width that is roughly twice the size of the most common objects in your game.

**Example:**

```cs
var hash = new SpatialHash<int>(16);
```

---

##### **public void Insert(T id, IShape2D shape, Transform2D Transform2D)**

Given an ID, a shape, and corresponding transform, inserts into the spatial hash. Uses the shape's AABB to insert into appropriate hash cells.

**Example:**

```cs
var hash = new SpatialHash<int>(16);

var circle = new MoonTools.Core.Bonk.Circle(8);
var circleTransform = new Transform2D(new Vector2(16, 16));

var rect = new Rectangle(-2, -2, 2, 2);
var rectTransform = new Transform2D(new Vector2(8, 8));

hash.Insert(0, circle, circleTransform);
hash.Insert(1, rect, rectTransform);
```

---

##### **public IEnumerable<(T, IShape2D, Transform2D)> Retrieve(T id, IShape2D shape, Transform2D Transform2D)**

Given an ID, a shape, and corresponding transform, retrieves a set of potential collisions from the spatial hash.

**Example:**

```cs
var hash = new SpatialHash<int>(16);

var circle = new MoonTools.Core.Bonk.Circle(8);
var circleTransform = new Transform2D(new Vector2(16, 16));

var rect = new Rectangle(-2, -2, 2, 2);
var rectTransform = new Transform2D(new Vector2(8, 8));

hash.Insert(0, circle, circleTransform);
hash.Insert(1, rect, rectTransform);

hash.Retrieve(1, rect, rectTransform);
```

In this example, the circle we inserted will be in the *IEnumerable* returned by the *Retrieve* call because they both exist in the same hash cell.

If a potential colliding shape-transform has the same ID as the one passed into the method, it will not be returned in the *IEnumerable*.

---

##### **public void Clear()**

Empties the spatial hash. Useful when the spatial hash contains dynamic data that needs to be updated.