---
title: "Position2D"
date: 2019-09-14T23:17:46-07:00
weight: 10
---

In 2D games, when it comes to rendering we are generally dealing with pixels. This presents us with certain challenges that don't exist in 3D. 

For example - what is half of a pixel? The pixel is the smallest possible unit in 2D rendering, so fractions of pixels don't really exist. 

This can present us with problems when it comes to game physics. If your character is at coordinates (2.5, 3.5), where do you draw the character? Is their sprite rounded up, or down? It might look strange if the rounding does not line up with your physics system.

To avoid these problems, I created the *Position2D* struct. *Position2D* maintains an integer X and Y position, as well as X and Y fractional carryover. Whenever numbers with fractional values are added to the position, the fractional values are added to the carryover. Once the carryover value reaches 1, it is added to the coordinate. This means that we can treat positions as integer values without sacrificing precision. 

Therefore, in our physics calculations, we will never have discrepancies between internal game position logic and rendering. 

```cs
var one = new Position2D(1.3f, 3.5f);
var two = new Position2D(4.8f, 0.9f);

var result = one + two; // result.X is 6, result.Y is 4
```

When we subtract *Position2D* vectors, this creates a *Vector2* representing motion, and the carryover values are used.

```cs
var one = new Position2D(1.3f, 3.5f);
var two = new Position2D(4.8f, 0.9f);

var result = one - two; // result.X is -3.5f, result.Y is 2.6f
```