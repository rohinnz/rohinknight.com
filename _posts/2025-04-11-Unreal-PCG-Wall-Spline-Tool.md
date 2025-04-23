---
layout: post
title:  "Unreal PCG Wall Spline Tool"
categories: techart
---

**This post currently has placeholder images and videos. I'm just waiting on the green light from PlaySide to include the actual media I'd like to share.**

{% include lightbox.html src="placeholder/image-placeholder.png" title="SPCG Wall Spline Tool" %}

I built this tool to allow level designers to place hidden wall collisions.

This tool places the optimal amount of box colliders alone the spline to ensure best performance. It also approrpiately adjusts the heigh of each collider depending on spline height change.

There is also a feature for adjusting the height in sections of a wall or cutting out part of a wall completely.

To build this tool I had to write two custom C++ PCG nodes and build one Blueprint PCG node.

{% include lightbox.html src="placeholder/video-placeholder.jpg" title="Unreal PCG Spline Tool" %}