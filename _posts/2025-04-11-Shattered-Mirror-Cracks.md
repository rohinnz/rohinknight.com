---
layout: post
title:  "Shattered Mirror Cracks"
categories: techart
---

At PlaySide I worked on [Shattered](https://www.meta.com/en-gb/experiences/shattered/5816339365118691/) (Unity - Quest 3 Mixed Reality)

One of my tasks was to make cracks grow on a mirror, eventually transitioning into shards falling out.

{% include youtube.html id="GrBdbaj5uL8" title="Shattered Mirror Cracks" %}

Depending on the situation, the crack needed to either:
* Split the mirror in half first, then grow outward
* Or grow evenly in all directions from the center

To achieve this, I created a custom mesh in Blender by tracing the glass shards that would fall out.

I tried two techniques to animate the crack, and ended up going with the second:

## Technique 1 - Distance-based reveal

I used a float parameter in the shader to control how much of the crack was visible, based on distance from the center. When needed, I added a bias to the Y-axis to grow the central split first.

While this was easy to set up, it didn’t look convincing:

* It was obvious the crack was simply being revealed by distance

* Pieces of the crack would appear before they were actually connected to the main split

## Technique 2 - Vertex color-based reveal

In this approach, the shader reveals the crack based on vertex color.

I wrote a Blender script that starts from a selected vertex and performs a flood fill across the crack mesh, assigning weights to each vertex as it spreads outward. These weights are normalized and stored as vertex colors.

For the split crack effect, I updated the script to handle a two-phase flood and created a group to store all the vertices that were part of the split.

With this setup, I could drive the animation with a 0–1 float value in the shader.

The result: both the cracks now grows in a much more natural way, and no disconnected pieces appear out of order.

<div style="display: flex; gap: 10px; align-items: flex-start;">
  <div style="flex: 1;">
    {% include lightbox.html src="shattered/normal-crack.gif" title="Shattered Mirror Normal Crack" %}
  </div>
  <div style="flex: 1;">
    {% include lightbox.html src="shattered/split-crack.gif" title="Shattered Mirror Split Crack" %}
  </div>
</div>

