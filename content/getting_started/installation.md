---
title: "Installation"
date: 2019-09-14T18:20:28-07:00
---

The simplest way of using Bonk is by including it in your C# project as a NuGet package.

To include the latest version of Bonk in your project using the .NET CLI, use the following command:

```sh
dotnet add package MoonTools.Core.Bonk
```

If you are using the NuGet Package Manager, you may do:

```sh
PM> Install-Package MoonTools.Core.Bonk
```

Once you have done this, you may access Bonk functionality by including

```cs
using MoonTools.Core.Bonk;
```

in any C# file.

Of course, you are free to include the source code directly in your project as well, but this is less convenient.