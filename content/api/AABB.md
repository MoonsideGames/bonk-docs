---
title: "AABB"
date: 2019-12-31T14:36:00-07:00
weight: 6
---

*AABB*, or axis-aligned bounding box, is defined by a minimum point and a maximum point. It is used for broad-phase collision detection. It represents a rectangular outline of the shape so we can quickly insert shapes into a *SpatialHash*.

## Properties

##### **public Vector2 Min { get; private set; }**

The minimum point of the AABB.

##### **public Vector2 Max { get; private set; }**

The maximum point of the AABB.

## Methods

##### **public static AABB FromVertices(IEnumerable<Position2D> vertices)**

Can be used to generate an AABB from an arbitrary collection of vertices. It is generally better to define a more efficient AABB generation method based on the properties of a particular shape, but this can be used for an arbitrary collection of vertices, like a polygon.

##### **public static AABB Transformed(AABB aabb, Transform2D transform)**

Efficiently transforms an AABB. Used internally by SpatialHash to quickly transform a shape's AABB.
