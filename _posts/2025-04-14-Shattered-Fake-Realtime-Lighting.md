---
layout: post
title:  "Fake Realtime Lighting"
categories: techart
---

In the game [Shattered](https://www.meta.com/en-gb/experiences/shattered/5816339365118691/) (Unity - Quest 3 Mixed Reality) there is no real-time lighting. This is due to hardware limitations.

Instead some neat tricks are used for stationary lights turning on/off and a flashlight you can shine anywhere!

# Lightmap Switching 💡 

{% include lightbox.html src="shattered/lightmap-switching.gif" title="Lightmap Switching" %}

For stationary lights, lightmaps are pre-baked for all possible combinations of a level. This approach is highly performant and works great with automated tooling.

While I wasn’t responsible for implementing the lightmap switching system, I did help out with some of the configuration and bug fixing.

# Torch 🔦

For the torch effect, I implemented lighting calculations in our custom shader and passed the torch’s position and direction as parameters.

The lighting logic was based on the "Light Casters" section from the LearnOpenGL website. I used this as a reference to correctly implement the spotlight-style falloff and intensity:
[https://learnopengl.com/Lighting/Light-casters](https://learnopengl.com/Lighting/Light-casters)

{% include lightbox.html src="shattered/learnopengl-diagram.png" title="Learn OpenGL Diagram" %}

I created and applied a custom cookie texture to the torch to achieve a more realistic, torch-like lighting effect. The cookie mask was based on a blurred image of a glass crack.

{% include lightbox.html src="shattered/original-torch-cookie.jpg" title="Torchlight cookie" %}

Here’s an early prototype of the torch in action. It looks nearly identical to real-time lighting—the only giveaway is the lack of shadows cast by the torchlight.

<video muted="true" loop="true" playsinline="true" autoplay="true" style="width: 100%; height: auto;">
  <source src="{{ site.baseurl }}/assets/videos/shattered-torch-prototype.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
<br />

# Flicker / Diming Effect 🕯️

I also added dynamic light luminance control so we could create flickering or dimming effects on various light sources.

Here’s an early prototype of that effect:

{% include lightbox.html src="shattered/shattered-dynamic-luminance.gif" title="Shattered Dynamic Luminance" %}
