---
layout: post
title:  "Color Swapping Technique in Three.JS"
categories: techart
---

**This post is under construction***

Example of color swapping shader technique using Three.JS. Click the buttons to change the character outfit and hair style.

<iframe 
  src="{{ '/colorswap/index.html' | relative_url }}" 
  width="100%" 
  height="600" 
  style="border: none;">
</iframe>

Shader Code:
```glsl
vec4 mask = texture(maskTex, vMapUv);

vec3 nonMasked = diffuseColor.rgb * (1.0 - (mask.r + mask.g + mask.b + mask.a));
vec3 tint =
  swapColor1 * mask.r +
  swapColor2 * mask.g + 
  swapColor3 * mask.b +
  swapColor4 * mask.a;

diffuseColor.rgb = nonMasked + (diffuseColor.rgb * tint);
```