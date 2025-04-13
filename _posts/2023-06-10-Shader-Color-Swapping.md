---
layout: post
title:  "Shader Color Swapping"
categories: techart
---

{% include lightbox.html src="resume/dmple-screenshot1.png" title="Dmple Game Screenshot" %}

I once needed to implement color swapping for a custom URP shader.

I achieved this by creating a simple mask and multiplying our custom colors by the mask’s RGB channels.

Since the mask texture has four channels (RGBA), there's always room for a fourth custom color later.

And if we ever need more than four custom colors, we can just introduce a second mask. 

This is similar to how terrain blending works.

Here’s the part of the shader that does the magic:

```hlsl
// Sample colors from both albedo texture and mask texture
half4 c = SAMPLE_TEXTURE2D(_BaseMap, sampler_BaseMap, input.uv);
half4 m = SAMPLE_TEXTURE2D(_MyMask, sampler_MyMask, input.uv);

half3 PrimaryColor = _PrimaryColor.rgb * m.r;
half3 SecondaryColor = _SecondaryColor.rgb * m.g;
half3 TertiaryColor = _TertiaryColor.rgb * m.b;

// Get non-masked color (part of albedo texture where we ignore mask)
half3 NonMasked = c.rgb * (1 - m.r - m.g - m.b);

half3 maskColors = PrimaryColor + SecondaryColor + TertiaryColor;

// Multiply maskColors with albedo and add non-masked
surfaceData.albedo = NonMasked + c.rgb * maskColors;
```

{% include lightbox.html src="resume/dmple-gameplay.gif" title="Dmple Gameplay" %}