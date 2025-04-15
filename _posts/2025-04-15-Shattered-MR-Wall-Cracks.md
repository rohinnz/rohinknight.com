---
layout: post
title:  "Shattered Mixed Reality Wall Cracks"
categories: techart
---

During early prototyping of Shattered (Meta - Mixed Reality Game), we experimented with placing cracks on the player’s wall that would open up with water gushing in, eventually filling the player’s room.

I created some cracks in Blender and used Shape Keys to animate them opening. In the image below, the front-facing polygons are set to blue and the back-facing polygons to red.
{% include lightbox.html src="shattered/blender-wall-cracks.png" title="Shattered Blender Wall Cracks" %}

Here’s an example of a test crack opening from top to bottom using Shape Keys.
{% include lightbox.html src="shattered/blender-wall-crack-opening.gif" title="Shattered Blender Wall Cracks" %}

To ensure that the front-facing polygons were only visible through the opening and hidden when the crack was closed, I created stencil mask meshes.

The stencil masks also needed Shape Keys to animate in sync with the cracks.

In this example, we have the crack mesh in a new scene. It disappears once we rotate it far enough that we can no longer see through the stencil mask.
{% include lightbox.html src="shattered/shattered-wall-crack-rotate.gif" title="Shattered Wall Crack Rotate" %}

And here’s the final result in a new scene. When the stencil mask is closed, the crack’s front-facing polygons are completely hidden.
{% include lightbox.html src="shattered/shattered-crack-opens.gif" title="Shattered Wall Crack Opens" %}
