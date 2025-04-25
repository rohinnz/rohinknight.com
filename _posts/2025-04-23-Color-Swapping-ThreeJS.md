---
layout: post
title:  "Color Swapping Technique in Three.js"
categories: techart
---

This is my first attempt at creating something with [Three.js](https://threejs.org/).

It is a character using the standard material with shader code injected for color swapping.

In the example below you can click the buttons to change the character outfit and hair style.

<iframe 
  src="{{ '/colorswap/index.html' | relative_url }}" 
  width="100%" 
  height="600" 
  style="border: none;">
</iframe>

To create this I decided to use the Prototype Pete created by [Kay Lousberg](https://kaylousberg.itch.io/).

{% include lightbox.html src="threejs/prototype-pete.png" title="" %}

The texture was a grid of gradients. I wanted to have 4 swappable colors so I added 4 white gradients.
{% include lightbox.html src="threejs/pete-texture.png" title="" %}

I then imported the model into blender and moved the UVs for the hair, shirt, pants and tie into the new white gradients.
{% include lightbox.html src="threejs/blender-move-uvs.png" title="" %}

I then created a copy of the texture for the mask and then deleted the existing gradients and replaced the new white gradients with red, green, blue and black.
{% include lightbox.html src="threejs/mask-texture.png" title="" %}

Then the most important step was to set the alpha for all of the mask to 0 except for the black square and then export with the "Save color values from transparent pixels" checked.
{% include lightbox.html src="threejs/gimp-mask.gif" title="" %}

And for the material I used the MeshStandardMaterial and modified the fragment shader function.

```typescript
const textureLoader = new THREE.TextureLoader();
const maskTexture = textureLoader.load('/colorswap/textures/pete_texture_mask.png');
const albedoTexture = textureLoader.load('/colorswap/textures/pete_texture.png');

const material = new THREE.MeshStandardMaterial({
  map: albedoTexture,
});

material.onBeforeCompile = (shader) => {
  material.userData.shader = shader;

  shader.uniforms.maskTex = { value: maskTexture };
  shader.uniforms.swapColor1 = { value: new THREE.Color(outfitColors[0][0]) };
  shader.uniforms.swapColor2 = { value: new THREE.Color(outfitColors[0][1]) };
  shader.uniforms.swapColor3 = { value: new THREE.Color(outfitColors[0][2]) };
  shader.uniforms.swapColor4 = { value: new THREE.Color(hairColors[0]) };

  //3b. Declare the sampler2D in fragment shader
  shader.fragmentShader = shader.fragmentShader.replace(
    /* glsl */`#include <common>`,
    /* glsl */`#include <common>
      uniform sampler2D maskTex;
      uniform vec3 swapColor1;
      uniform vec3 swapColor2;
      uniform vec3 swapColor3;
      uniform vec3 swapColor4;
  `);

  shader.fragmentShader = shader.fragmentShader.replace(
    /* glsl */`#include <color_fragment>`,
    /* glsl */`#include <color_fragment>
    vec4 mask = texture(maskTex, vMapUv);
    
    vec3 nonMasked = diffuseColor.rgb * (1.0 - (mask.r + mask.g + mask.b + mask.a));
    vec3 tint =
      swapColor1 * mask.r +
      swapColor2 * mask.g + 
      swapColor3 * mask.b +
      swapColor4 * mask.a;
    
    diffuseColor.rgb = nonMasked + (diffuseColor.rgb * tint);
  `);

  // todo: Uncomment to debug generated shader code
  /*
  console.log('vertex shader');
  console.log(shader.vertexShader);
  console.log('fragment shader');
  console.log(shader.fragmentShader);
  */
}

```