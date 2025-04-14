---
layout: post
title:  "Shattered Fake Realtime Lighting"
categories: techart
---

Shattered is a Meta Mixed Reality game and one of the most important parts of the gameplay is the flashlight.

Due to hardware limitations, we could not use real-time lighting in the game.

So in order to create a torchlight effect, I had to implement some fake lighting. It looks almost the same as real-time lighting except for the lack of real-time shadows.

On the OpenGL website there is a great article on how to do the lighting calculations for the spotlight.

[https://learnopengl.com/Lighting/Light-casters](https://learnopengl.com/Lighting/Light-casters)

I also created and applied a cookie to the torch to give the lighting more of a torchlike look.

Here is an early prototype of the torch:

{% include lightbox.html src="shattered/shattered-torch-prototype.gif" title="Shattered Torch Prototype" %}

I also added dynamic light luminance so we could add a flicker/diming type effect to other light sources.

Here is an early prototype showing this feature:

{% include lightbox.html src="shattered/shattered-dynamic-luminance.gif" title="Shattered Dynamic Luminance" %}
