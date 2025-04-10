---
layout: post
title:  "Unreal PCG Wall Spline Tool"
categories: tooling
---

I built this tool to allow level designers to place hidden wall collisions.

This tool places the optimal amount of box colliders alone the spline to ensure best performance. It also approrpiately adjusts the heigh of each collider depending on spline height change.

There is also a feature for adjusting the height in sections of a wall or cutting out part of a wall completely.

To build this tool I had to write two custom C++ PCG nodes and build one Blueprint PCG node.

<video style="width: 100%; height: auto;" controls>
  <source src="{{ site.baseurl }}/assets/videos/PCG-Wall-Spline-Tool.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>