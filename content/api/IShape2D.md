---
title: "IShape2D"
date: 2019-09-15T11:06:50-07:00
weight: 5
---

An *IShape2D* is an interface that, when implemented, allows for spatial hashing and the computation of Minkowski Differences.

Your *IShape2D* types should be structs for memory efficiency purposes.

## Methods

##### **Vector2 Support(Vector2 direction, Transform2D transform)**

A method which implements a support function for use with a Minkowski Difference.

The support function must, given a directional vector and a Transform2D, return the farthest possible vertex of the transformed shape in the given direction.

For example, the support function for Bonk's *Circle* implementation:

```cs
public Vector2 Support(Vector2 direction, Transform2D transform)
{
    return Vector2.Transform(Vector2.Normalize(direction) * Radius, transform.TransformMatrix);
}
```

---

##### **AABB AABB(Transform2D transform)**

A method which returns the axis-aligned bounding box for the transformed shape.

For example, the AABB method for Bonk's *Circle* implementation:

```cs
public AABB AABB(Transform2D Transform2D)
{
    return new AABB(
        Transform2D.Position.X - Radius,
        Transform2D.Position.Y - Radius,
        Transform2D.Position.X + Radius,
        Transform2D.Position.Y + Radius
    );
}
```