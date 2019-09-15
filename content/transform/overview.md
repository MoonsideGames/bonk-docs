---
title: "Overview"
date: 2019-09-14T23:08:31-07:00
weight: 5
---

Bonk uses the *Transform2D* struct which is taken from the MoonTools.Core.Structs package. By extension it also uses the *Position2D* struct taken from the same package.

A *Transform2D* is basically a way to store information about an object's location, rotation, and scale in 2-dimensional space. Transforms use matrix math to perform all of these operations at once, making them very fast.

For memory performance purposes, shapes are implemented as structs, meaning they are value types. This means that it is much easier to deal with collision using a transform applied to a shape, rather than containing a transform within the shape. 

It is also often the case that you will have a shape attached to a game object that is offset from the object by a certain amount. A *Transform2D* can represent this information as well, since *Tranform2Ds* can be composed together. As you can see, a *Transform2D* provides a generic structure for dealing with many scenarios involving 2D space.

