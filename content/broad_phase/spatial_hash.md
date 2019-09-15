---
title: "Spatial Hash"
date: 2019-09-14T18:35:33-07:00
weight: 10
---

In spatial hashing, we place each object into one or more "buckets". Think of a grid covering 2D space. When an object's bounding box covers one of the cells in this grid, it is placed into that cell. Any two unique objects that occupy the same cell are determined to be *potentially colliding*.

In Bonk, a spatial hash is defined by its ID type and a cell size. The ID type is used to filter objects. Any two objects with the same ID are assumed to not be colliding.

```cs
var hash = new SpatialHash<Guid>(32);
```

This spatial hash will use C# **GUID**s as its ID type and a cell size of 32.

To insert an object into the hash, use the **Insert** method and give an ID, an IShape2D, and a Transform2D.

```cs
var hash = new SpatialHash<int>(16);

var circle = new MoonTools.Core.Bonk.Circle(8);
var circleTransform = new Transform2D(new Vector2(16, 16));

var rect = new Rectangle(-2, -2, 2, 2);
var rectTransform = new Transform2D(new Vector2(8, 8));

hash.Insert(0, circle, circleTransform);
hash.Insert(1, rect, rectTransform);
```

To find potential collisions, use the **Retrieve** method and give an ID, an IShape2D, and a Transform2D.

```cs
spatialHash.Retrieve(1, rectB, rectBTransform);
```

In this example, the above method call returns an *IEnumerable<(T, IShape2D, Transform)>* containing the circle information we inserted.

What if we want to update our SpatialHash based on the movements of objects? Simply clear the hash and insert all the objects again.

```cs
hash.Clear();

// Re-insert objects here
```

That's it! This is everything you need to use a spatial hash for broad-phase collision.