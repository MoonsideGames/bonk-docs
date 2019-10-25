---
title: "Bonk"
---

# Bonk

[Bonk](https://github.com/MoonsideGames/MoonTools.Core.Bonk) is a fast and modular collision detection system for MonoGame that is part of the MoonTools suite.

Bonk **is** designed to help you figure out if two shapes are overlapping and by how much.

Bonk **is not** a physics simulator and it will not help you execute collision responses. 

Bonk is designed for performance and memory efficiency. Defining most shapes and performing collision tests require no heap allocations and thus put no pressure on the garbage collector. If you reuse spatial hashes and avoid using arbitrary polygons, Bonk will never cause garbage collection.

Bonk is available as a [NuGet package](https://www.nuget.org/packages/MoonTools.Core.Bonk/).

Bonk is licensed under the [LGPL-3](https://www.gnu.org/licenses/lgpl-3.0.en.html) license. In summary: feel free to include it in your closed-source game and modify it internally at will, but if you make changes that you intend to redistribute, you **must** freely publish your changes.